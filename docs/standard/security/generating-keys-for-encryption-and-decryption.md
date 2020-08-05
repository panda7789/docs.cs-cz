---
title: Generování klíčů pro šifrování a dešifrování
description: Naučte se vytvářet a spravovat symetrický a asymetrický klíč pro šifrování a dešifrování v .NET.
ms.date: 07/14/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- keys, encryption and decryption
- keys, asymmetric
- keys, symmetric
- encryption [.NET], keys
- symmetric keys
- asymmetric keys [.NET]
- cryptography [.NET], keys
ms.assetid: c197dfc9-a453-4226-898d-37a16638056e
ms.openlocfilehash: 7ce19dc465fb1fac22545398e0724e6b76dd7098
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556940"
---
# <a name="generating-keys-for-encryption-and-decryption"></a>Generování klíčů pro šifrování a dešifrování
Vytváření a správa klíčů je důležitou součástí procesu šifrování. Symetrické algoritmy vyžadují vytvoření klíče a inicializačního vektoru (IV). Klíč musí být udržen v tajnosti před kýmkoli, kdo by neměl data dešifrovat. Vektor IV nemusí být tajný, ale měli byste jej pro jednotlivé relace změnit. Asymetrické algoritmy vyžadují vytvoření veřejného klíče a soukromého klíče. Veřejný klíč se může zveřejnit všem uživatelům, zatímco soukromý klíč smí být znám pouze osobě, která bude dešifrovat data zašifrovaná pomocí veřejného klíče. V této části je popsán způsob vytváření a správy klíčů pro symetrické i asymetrické algoritmy.  
  
## <a name="symmetric-keys"></a>Symetrické klíče  
 Třídy symetrického šifrování dodávané rozhraním .NET vyžadují klíč a nový inicializační vektor (IV) pro šifrování a dešifrování dat. Kdykoli vytvoříte novou instanci jedné ze spravovaných symetrických kryptografických tříd pomocí metody bez parametrů `Create()` , automaticky se vytvoří nový klíč a IV. Jakákoli osoba s oprávněním k dešifrování dat musí mít stejný klíč a vektor IV a použít stejný algoritmus. Obecně lze říci, že nový klíč a vektor IV by měly být vytvořeny pro každou relaci a klíč ani vektor IV by neměly být ukládány pro používání v pozdější relaci.  
  
 Ke sdělení symetrického klíče a vektoru IV vzdálené straně je obvykle třeba zašifrovat symetrický klíč pomocí asymetrického šifrování. Odesílání klíče v nezabezpečené síti bez šifrování je velmi nebezpečné, jelikož jakákoli osoba, která klíč a vektor IV zachytí, může data dešifrovat.  
  
 Následující příklad ukazuje vytvoření nové instance výchozí třídy implementace pro <xref:System.Security.Cryptography.Aes> algoritmus.  
  
```vb  
Dim aes As Aes = Aes.Create()  
```  
  
```csharp  
Aes aes = Aes.Create();  
```  
  
 Když se spustí předchozí kód, vygeneruje se nový klíč a IV a umístí se do vlastností **Key** a **IV** v uvedeném pořadí.  
  
 Občas bude pravděpodobně nutné generovat více klíčů. V této situaci můžete vytvořit novou instanci třídy, která implementuje symetrický algoritmus, a pak vytvořit nový klíč a IV voláním metod **GenerateKey** a **GenerateIV** . Následující příklad kódu ukazuje, jak vytvořit nové klíče a Ideographic po provedení nové instance symetrické kryptografické třídy.  
  
```vb  
Dim aes As Aes = Aes.Create()  
aes.GenerateIV()  
aes.GenerateKey()  
```  
  
```csharp  
Aes aes = Aes.Create();  
aes.GenerateIV();  
aes.GenerateKey();  
```  
  
 Když je proveden předchozí kód, klíč a IV jsou generovány při vytvoření nové instance **AES** . Při volání metod **GenerateKey** a **GenerateIV** se vytvoří další klíč a IV.
  
## <a name="asymmetric-keys"></a>Asymetrické klíče

 Rozhraní .NET poskytuje <xref:System.Security.Cryptography.RSA> třídu pro asymetrické šifrování. Tato třída vytvoří pár veřejného a privátního klíče, pokud použijete metodu bez parametrů `Create()` k vytvoření nové instance. Asymetrické klíče mohou být buď uloženy pro použití ve více relacích, nebo generovány pouze pro jednu relaci. Zatímco veřejný klíč může být zpřístupněn veřejně, soukromý klíč by měl být přísně chráněný.  
  
 Pár veřejného/soukromého klíče je generován při každém vytvoření nové instance třídy asymetrického algoritmu. Po vytvoření nové instance třídy mohou být informace o klíči extrahovány pomocí <xref:System.Security.Cryptography.RSA.ExportParameters%2A> metody, která vrací <xref:System.Security.Cryptography.RSAParameters> strukturu, která obsahuje informace o klíči. Metoda přijímá logickou hodnotu, která označuje, jestli se mají vracet jenom informace o veřejném klíči, nebo jestli se mají vracet informace o veřejném klíči i s privátním klíčem.

Existují také jiné metody, které umožňují extrahování klíčových informací, například:

* <xref:System.Security.Cryptography.RSA.ExportRSAPublicKey%2A?displayProperty=nameWithType>
* <xref:System.Security.Cryptography.RSA.ExportRSAPrivateKey%2A?displayProperty=nameWithType>
* <xref:System.Security.Cryptography.AsymmetricAlgorithm.ExportSubjectPublicKeyInfo%2A?displayProperty=nameWithType>
* <xref:System.Security.Cryptography.AsymmetricAlgorithm.ExportPkcs8PrivateKey%2A?displayProperty=nameWithType>
* <xref:System.Security.Cryptography.AsymmetricAlgorithm.ExportEncryptedPkcs8PrivateKey%2A?displayProperty=nameWithType>

Instance **RSA** může být inicializována na hodnotu struktury **RSAParameters** pomocí <xref:System.Security.Cryptography.RSA.ImportParameters%2A> metody. Nebo vytvořte novou instanci pomocí <xref:System.Security.Cryptography.RSA.Create(System.Security.Cryptography.RSAParameters)?displayProperty=nameWithType> metody.  
  
 Asymetrické soukromé klíče by nikdy neměly být uloženy doslovně nebo ve formátu prostého textu v místním počítači. Pokud potřebujete uložit soukromý klíč, měli byste použít kontejner klíčů. Další informace o tom, jak uložit privátní klíč do kontejneru klíčů, naleznete v tématu [How to: Store asymetrické klíče in a Key Container](how-to-store-asymmetric-keys-in-a-key-container.md).  
  
 Následující příklad kódu vytvoří novou instanci třídy **RSA** , vytvoří dvojici veřejného a privátního klíče a uloží informace o veřejném klíči do struktury **RSAParameters** .  
  
```vb  
'Generate a public/private key pair.  
Dim rsa as RSA = RSA.Create()  
'Save the public key information to an RSAParameters structure.  
Dim rsaKeyInfo As RSAParameters = rsa.ExportParameters(false)  
```  
  
```csharp  
//Generate a public/private key pair.  
RSA rsa = RSA.Create();  
//Save the public key information to an RSAParameters structure.  
RSAParameters rsaKeyInfo = rsa.ExportParameters(false);  
```  
  
## <a name="see-also"></a>Viz také

- [Šifrování dat](encrypting-data.md)
- [Dešifrování dat](decrypting-data.md)
- [Šifrovací služby](cryptographic-services.md)
- [Postupy: Uložení asymetrického klíče v kontejneru klíčů](how-to-store-asymmetric-keys-in-a-key-container.md)
- [Kryptografie pro různé platformy](cross-platform-cryptography.md)
- [Ochrana dat ASP.NET Core](/aspnet/core/security/data-protection/introduction)
