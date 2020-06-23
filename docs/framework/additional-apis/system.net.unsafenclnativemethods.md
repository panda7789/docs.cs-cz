---
title: UnsafeNclNativeMethods – třída (System.Net)
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.UnsafeNclNativeMethods
- System.Net.UnsafeNclNativeMethods.NativePKI
- System.Net.UnsafeNclNativeMethods.NativePKI.FindClientCertificates
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: 46756a0d1d69b4768dbb8dcdd7ab098d3f1849bf
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990325"
---
# <a name="unsafenclnativemethods-class"></a><span data-ttu-id="4db69-102">UnsafeNclNativeMethods – třída</span><span class="sxs-lookup"><span data-stu-id="4db69-102">UnsafeNclNativeMethods class</span></span>

<span data-ttu-id="4db69-103">Obsahuje třídy, které importují nebezpečné nativní síťové metody.</span><span class="sxs-lookup"><span data-stu-id="4db69-103">Contains classes that import unsafe native networking methods.</span></span> <span data-ttu-id="4db69-104">Tuto třídu nelze zdědit.</span><span class="sxs-lookup"><span data-stu-id="4db69-104">This class cannot be inherited.</span></span>

```csharp
internal static class UnsafeNclNativeMethods
```

> [!WARNING]
> <span data-ttu-id="4db69-105">Tato třída je interní a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="4db69-105">This class is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="4db69-106">Společnost Microsoft v žádné situaci nepodporuje použití této třídy v produkční aplikaci.</span><span class="sxs-lookup"><span data-stu-id="4db69-106">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="nativepki-class"></a><span data-ttu-id="4db69-107">NativePKI – třída</span><span class="sxs-lookup"><span data-stu-id="4db69-107">NativePKI class</span></span>

<span data-ttu-id="4db69-108">Obsahuje metody importované z crypt32.dll.</span><span class="sxs-lookup"><span data-stu-id="4db69-108">Contains methods imported from crypt32.dll.</span></span> <span data-ttu-id="4db69-109">Tyto metody zpracovávají certifikáty při použití protokolu HTTPS (Hypertext Transfer Protocol Secure).</span><span class="sxs-lookup"><span data-stu-id="4db69-109">These methods handle certificates when using Hypertext Transfer Protocol Secure (HTTPS).</span></span> <span data-ttu-id="4db69-110">Tuto třídu nelze zdědit.</span><span class="sxs-lookup"><span data-stu-id="4db69-110">This class cannot be inherited.</span></span>

```csharp
internal static class NativePKI
```

## <a name="nativepkifindclientcertificates-method"></a><span data-ttu-id="4db69-111">NativePKI. FindClientCertificates – metoda</span><span class="sxs-lookup"><span data-stu-id="4db69-111">NativePKI.FindClientCertificates method</span></span>

<span data-ttu-id="4db69-112">Zjišťuje dostupné klientské certifikáty pro odeslání na server.</span><span class="sxs-lookup"><span data-stu-id="4db69-112">Discovers available client certificates to send to the server.</span></span>

```csharp
internal static X509CertificateCollection FindClientCertificates
```

### <a name="return-value"></a><span data-ttu-id="4db69-113">Vrácená hodnota</span><span class="sxs-lookup"><span data-stu-id="4db69-113">Return value</span></span>

<xref:System.Security.Cryptography.X509Certificates.X509CertificateCollection?displayProperty=nameWithType>

<span data-ttu-id="4db69-114">Kolekce dostupných klientských certifikátů.</span><span class="sxs-lookup"><span data-stu-id="4db69-114">A collection of available client certificates.</span></span>

## <a name="requirements"></a><span data-ttu-id="4db69-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4db69-115">Requirements</span></span>

<span data-ttu-id="4db69-116">**Obor názvů:**<xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="4db69-116">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="4db69-117">**Sestavení:** Systém (v System.dll)</span><span class="sxs-lookup"><span data-stu-id="4db69-117">**Assembly:** System (in System.dll)</span></span>
