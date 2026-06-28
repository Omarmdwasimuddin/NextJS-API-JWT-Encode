## NextJS API---> JWT Encode

#### Visit---> https://www.jwt.io/ --->click: Libraries
#### Or, Visit---> https://www.npmjs.com/package/jose 
### install
```bash
npm install jose
```
---

### /app/api/token
![]()

```bash
import { SignJWT } from "jose";
import { NextRequest, NextResponse } from "next/server";



export async function GET(request:NextRequest) {
    
    const Key = new TextEncoder().encode(process.env.JWT_KEY);
    const payload = { email: "abc@gmail.com", user_id: "ABC123" };

    let token = await new SignJWT(payload)
        .setProtectedHeader({ alg: 'HS256' })
        .setIssuedAt()
        .setIssuer('https://localhost:3000')
        .setExpirationTime('2h')
        .sign(Key)

    return NextResponse.json(
        {token: token},
        {status: 200}
    )
}
```
### .env
```bash
JWT_KEY=aabcc00xyz123hello987demo
```
---
