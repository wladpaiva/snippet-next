# Next.js 14 Extension Snippets

This is a collection of useful code snippets to speed up development in `Next.js 14` (`app`) directory.

## Usage

Tab trigger snippets are available for the following languages: `TypeScript React`, `Javascript React`.

[![](https://img.shields.io/visual-studio-marketplace/i/yuzu.snippets-next-13?label=Market%20download&style=for-the-badge)](https://marketplace.visualstudio.com/items?itemName=yuzu.snippets-next-13)

## Features

| Command                                                     | Description                                                        |
| ----------------------------------------------------------- | ------------------------------------------------------------------ |
| [`next-prc`](#page-component)                               | Create a new page component.                                       |
| [`next-lmrc`](#layout-root-and-metadata-component)          | Create a new layout root component with metadata.                  |
| [`next-lrc`](#layout-root-component)                        | Create a new layout root component.                                |
| [`next-crc`](#client-component)                             | Create a new client component.                                     |
| [`next-mr`](#metadata)                                      | Create a new metadata.                                             |
| [`next-gmrf`](#generatemetadata)                            | Create a new generateMetaData for SEO.                             |
| [`next-gsp`](#generatestaticparams-for-dynamic-page-static) | Create a new generateStaticParams function for dynamic page static |
| [`next-rag`](#route-handler-api-get)                        | Create a function Route Handler API GET.                           |
| [`next-ragd`](#route-handler-api-get-with-dynamic)          | Create a function Route Handler API GET with Dynamic.              |
| [`next-rags`](#route-handler-api-get-and-search)            | Create a function Route Handler API GET and Search.                |
| [`next-rap`](#route-handler-api-post)                       | Create a function Route Handler API POST.                          |
| [`next-rau`](#route-handler-api-update)                     | Create a function Route Handler API UPDATE.                        |
| [`next-rad`](#route-handler-api-delete)                     | Create a function Route Handler API DELETE.                        |
| [`next-load`](#loading)                                     | Create a Loading component                                         |
| [`next-err`](#error)                                        | Create a Error component with error handling and recovery          |

## Full Snippets

### Page Component

Prefix: `next-prc`

```tsx
export default function ${Name}Page() {
  return (
    <div>
      <h1>Hello Page</h1>
    </div>
  );
}

```

### Layout Component

Prefix: `next-lrc`

```tsx

export default function ${Root Name}Layout({
  children,
}: {
  children: React.ReactNode;
}) {
  return (
    <div>
      <h1>Hello Root Layout</h1>
    </div>
  );
}


```

### Client Component

Prefix: `next-crc`

```tsx

'use client';

export default function ${Name}() {
  return (
    <div>
      <h1>Client Component</h1>
    </div>
  );
}


```

### Layout and Metadata Component

Prefix: `next-lmrc`

```tsx
export const metadata = {
  title: '${Title}',
  description: '${Description}',
};
export default function ${Root Name}Layout({
  children,
}: {
  children: React.ReactNode;
}) {
  return (
    <div>
      <h1>Hello Root and MetaData ${Name}</h1>
    </div>
  );
}


```

### Metadata

Prefix: `next-mr`

```tsx
export const metadata = {
  title: "${Title}",
  description: "${Description}",
};
```

### generateMetaData

Prefix: `next-gmrf`

```tsx

import type { Metadata } from 'next';

export async function generateMetadata({
  params,
}: {
  params: { ${slug} };
}): Promise<Metadata> {
  const product = await ${getData}(${slug});
  return { title: product.title };
}


```

### generateStaticParams for Dynamic Page Static

Prefix: `next-gsp`

```tsx
export async function generateStaticParams() {
  const posts = await fetch("${fetch url}").then((res) => res.json());

  return posts.map((post) => ({
    slug: post.slug,
  }));
}
```

### Route Handler API GET

Prefix: `next-rag`

```ts
import { NextResponse, NextRequest } from 'next/server';

export async function GET(request: Request, context: { params: { ${slug}: string } }) {

  const { ${slug} } = context.params;
}

```

### Route Handler API GET with Dynamic

Prefix: `next-ragd`

```ts

import { NextResponse, NextRequest } from 'next/server';

export async function GET(request: Request, context: { params: { ${slug}: string } }) {

  const { ${slug} } = context.params;
}

```

### Route Handler API GET and Search

Prefix: `next-rags`

```ts
import { NextResponse, NextRequest } from "next/server";

export async function GET(request: Request) {
  const url = new URL(req.url).searchParams;
  const id = Number(url.get("id"));
  // Example: http://localhost:3000/api/posts?id=1
}
```

### Route Handler API POST

Prefix: `next-rap`

```ts
import { NextResponse, NextRequest } from "next/server";
export async function POST(request: Request) {
  // this request body is a JSON object
  const { title } = await req.json();
  return new NextResponse.json({ title }, { status: 201 });
}
```

### Route Handler API UPDATE

Prefix: `next-rau`

```ts
import { NextResponse, NextRequest } from "next/server";
export async function PUT(request: Request) {
  // this request body is a JSON object
  const { title } = await req.json();
  return new NextResponse.json({ title }, { status: 201 });
}
```

### Route Handler API DELETE

Prefix: `next-rad`

```ts
import { NextResponse, NextRequest } from "next/server";
export async function DELETE(request: Request) {
  // your function here
}
```

### Loading

Prefix: `next-load`

```tsx
export default function Loading() {
  return <div>Loading...</div>;
}
```

### Error

Prefix: `next-err`

```tsx
"use client";
import { useEffect } from "react";

export default function Error({
  error,
  reset,
}: {
  error: Error;
  reset: () => void;
}) {
  useEffect(() => {
    // Log the error
    console.error(error);
  }, [error]);

  return (
    <div>
      <h2>Something went wrong!</h2>
      <button onClick={() => reset()}>Try again</button>
    </div>
  );
}
```

## Known Issues

Calling out known issues can help limit users opening duplicate issues against your extension.

## Contributing

Contributions are welcome! If you have a useful code snippet that you'd like to share, simply open a pull request and we'll review it as soon as possible.

**Enjoy!**
