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
# <a name="unsafenclnativemethods-class"></a>UnsafeNclNativeMethods – třída

Obsahuje třídy, které importují nebezpečné nativní síťové metody. Tuto třídu nelze zdědit.

```csharp
internal static class UnsafeNclNativeMethods
```

> [!WARNING]
> Tato třída je interní a není určena pro použití přímo v kódu.
>
> Společnost Microsoft v žádné situaci nepodporuje použití této třídy v produkční aplikaci.

## <a name="nativepki-class"></a>NativePKI – třída

Obsahuje metody importované z crypt32.dll. Tyto metody zpracovávají certifikáty při použití protokolu HTTPS (Hypertext Transfer Protocol Secure). Tuto třídu nelze zdědit.

```csharp
internal static class NativePKI
```

## <a name="nativepkifindclientcertificates-method"></a>NativePKI. FindClientCertificates – metoda

Zjišťuje dostupné klientské certifikáty pro odeslání na server.

```csharp
internal static X509CertificateCollection FindClientCertificates
```

### <a name="return-value"></a>Vrácená hodnota

<xref:System.Security.Cryptography.X509Certificates.X509CertificateCollection?displayProperty=nameWithType>

Kolekce dostupných klientských certifikátů.

## <a name="requirements"></a>Požadavky

**Obor názvů:**<xref:System.Net>

**Sestavení:** Systém (v System.dll)
