# Product-listing-page
import axios from 'axios';
import Header from '../components/Header';
import ProductGrid from '../components/ProductGrid';
import Footer from '../components/Footer';

export default function Home({ products }) {
  return (
    <>
      <Header />
      <ProductGrid products={products} />
      <Footer />
    </>
  );
}

export async function getServerSideProps() {
  const res = await axios.get('https://fakestoreapi.com/products');
  return {
    props: { products: res.data },
  };
}


export default function Header() {
  return (
    <header className="bg-white shadow p-4 flex justify-between items-center">
      <h1 className="text-xl font-bold">Product Store</h1>
      <div>
        <a href="/signin" className="mr-4 text-blue-600">Sign In</a>
        <a href="/signup" className="text-blue-600">Sign Up</a>
      </div>
    </header>
  );
}


import ProductCard from './ProductCard';

export default function ProductGrid({ products }) {
  return (
    <div className="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-6 p-6">
      {products.map(product => (
        <ProductCard key={product.id} product={product} />
      ))}
    </div>
  );
}


export default function ProductCard({ product }) {
  return (
    <div className="border p-4 rounded-md shadow hover:scale-105 transition">
      <img src={product.image} alt={product.title} className="w-full h-40 object-contain" />
      <h2 className="text-md mt-2 font-medium">{product.title}</h2>
      <p className="text-sm text-gray-500">${product.price}</p>
    </div>
  );
}


export default function Footer() {
  return (
    <footer className="bg-gray-100 text-center p-4 mt-6">
      <p className="text-sm text-gray-500">© 2025 Product Store. All rights reserved.</p>
    </footer>
  );
}


export default function SignIn() {
  return (
    <div className="p-6 max-w-md mx-auto">
      <h1 className="text-2xl font-bold mb-4">Sign In</h1>
      <input type="email" placeholder="Email" className="w-full border p-2 mb-4" />
      <input type="password" placeholder="Password" className="w-full border p-2 mb-4" />
      <button className="w-full bg-blue-600 text-white py-2 rounded">Sign In</button>
    </div>
  );
}


export default function SignUp() {
  return (
    <div className="p-6 max-w-md mx-auto">
      <h1 className="text-2xl font-bold mb-4">Sign Up</h1>
      <input type="text" placeholder="Name" className="w-full border p-2 mb-4" />
      <input type="email" placeholder="Email" className="w-full border p-2 mb-4" />
      <input type="password" placeholder="Password" className="w-full border p-2 mb-4" />
      <button className="w-full bg-green-600 text-white py-2 rounded">Sign Up</button>
    </div>
  );
}


@tailwind base;
@tailwind components;
@tailwind utilities;
