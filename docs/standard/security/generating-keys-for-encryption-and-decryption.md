---
title: Generování klíčů pro šifrování a dešifrování
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- keys, encryption and decryption
- keys, asymmetric
- keys, symmetric
- encryption [.NET Framework], keys
- symmetric keys
- asymmetric keys [.NET Framework]
- cryptography [.NET Framework], keys
ms.assetid: c197dfc9-a453-4226-898d-37a16638056e
ms.openlocfilehash: 992ac30310d138e04b8408497c5e49166a356ab4
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291536"
---
# <a name="generating-keys-for-encryption-and-decryption"></a>Generování klíčů pro šifrování a dešifrování
Vytváření a správa klíčů je důležitou součástí procesu šifrování. Symetrické algoritmy vyžadují vytvoření klíče a inicializačního vektoru (IV). Klíč musí být udržen v tajnosti před kýmkoli, kdo by neměl data dešifrovat. Vektor IV nemusí být tajný, ale měli byste jej pro jednotlivé relace změnit. Asymetrické algoritmy vyžadují vytvoření veřejného klíče a soukromého klíče. Veřejný klíč se může zveřejnit všem uživatelům, zatímco soukromý klíč smí být znám pouze osobě, která bude dešifrovat data zašifrovaná pomocí veřejného klíče. V této části je popsán způsob vytváření a správy klíčů pro symetrické i asymetrické algoritmy.  
  
## <a name="symmetric-keys"></a>Symetrické klíče  
 Třídy pro symetrické šifrování poskytované rozhraním .NET Framework vyžadují klíč a nový inicializační vektor (IV) k šifrování a dešifrování dat. Kdykoli vytvoříte novou instanci jedné ze spravovaných symetrických kryptografických tříd pomocí konstruktoru bez parametrů, automaticky se vytvoří nový klíč a IV. Jakákoli osoba s oprávněním k dešifrování dat musí mít stejný klíč a vektor IV a použít stejný algoritmus. Obecně lze říci, že nový klíč a vektor IV by měly být vytvořeny pro každou relaci a klíč ani vektor IV by neměly být ukládány pro používání v pozdější relaci.  
  
 Ke sdělení symetrického klíče a vektoru IV vzdálené straně je obvykle třeba zašifrovat symetrický klíč pomocí asymetrického šifrování. Odesílání klíče v nezabezpečené síti bez šifrování je velmi nebezpečné, jelikož jakákoli osoba, která klíč a vektor IV zachytí, může data dešifrovat. Další informace o výměně dat pomocí šifrování najdete v tématu [Vytvoření kryptografického schématu](creating-a-cryptographic-scheme.md).  
  
 Následující příklad znázorňuje vytvoření nové instance třídy <xref:System.Security.Cryptography.TripleDESCryptoServiceProvider>, která implementuje algoritmus TripleDES.  
  
```vb  
Dim tdes As TripleDESCryptoServiceProvider = new TripleDESCryptoServiceProvider()  
```  
  
```csharp  
TripleDESCryptoServiceProvider tdes = new TripleDESCryptoServiceProvider();  
```  
  
 Když se spustí předchozí kód, vygeneruje se nový klíč a IV a umístí se do vlastností **Key** a **IV** v uvedeném pořadí.  
  
 Občas bude pravděpodobně nutné generovat více klíčů. V této situaci můžete vytvořit novou instanci třídy, která implementuje symetrický algoritmus, a pak vytvořit nový klíč a IV voláním metod **GenerateKey** a **GenerateIV** . Následující příklad kódu ukazuje, jak vytvořit nové klíče a Ideographic po provedení nové instance symetrické kryptografické třídy.  
  
```vb  
Dim tdes As TripleDESCryptoServiceProvider = new TripleDESCryptoServiceProvider()  
tdes.GenerateIV()  
tdes.GenerateKey()  
```  
  
```csharp  
TripleDESCryptoServiceProvider tdes = new TripleDESCryptoServiceProvider();  
tdes.GenerateIV();  
tdes.GenerateKey();  
```  
  
 Když je proveden předchozí kód, klíč a IV jsou generovány při vytvoření nové instance **TripleDESCryptoServiceProvider** . Při volání metod **GenerateKey** a **GenerateIV** se vytvoří další klíč a IV.  
  
## <a name="asymmetric-keys"></a>Asymetrické klíče  
 Rozhraní .NET Framework poskytuje třídy <xref:System.Security.Cryptography.RSACryptoServiceProvider> a <xref:System.Security.Cryptography.DSACryptoServiceProvider> pro asymetrické šifrování. Tyto třídy vytvoří pár veřejného a privátního klíče, pokud použijete konstruktor bez parametrů k vytvoření nové instance. Asymetrické klíče mohou být buď uloženy pro použití ve více relacích, nebo generovány pouze pro jednu relaci. Zatímco veřejný klíč může být zpřístupněn veřejně, soukromý klíč by měl být přísně chráněný.  
  
 Pár veřejného/soukromého klíče je generován při každém vytvoření nové instance třídy asymetrického algoritmu. Po vytvoření nové instance třídy může být informace o klíči extrahována pomocí jedné ze dvou metod:  
  
- <xref:System.Security.Cryptography.RSA.ToXmlString%2A>Metoda, která vrátí reprezentaci informací o klíči XML.  
  
- Metodou <xref:System.Security.Cryptography.RSACryptoServiceProvider.ExportParameters%2A>, která vrátí strukturu <xref:System.Security.Cryptography.RSAParameters> s informacemi o klíči.  
  
 Obě metody přijímají logickou hodnotu, která označuje, zda vrátit informace pouze o veřejném klíči nebo zda vrátit také informace o veřejném klíči a soukromém klíči. Třída **RSACryptoServiceProvider** může být inicializována na hodnotu struktury **RSAParameters** pomocí <xref:System.Security.Cryptography.RSACryptoServiceProvider.ImportParameters%2A> metody.  
  
 Asymetrické soukromé klíče by nikdy neměly být uloženy doslovně nebo ve formátu prostého textu v místním počítači. Pokud potřebujete uložit soukromý klíč, měli byste použít kontejner klíčů. Další informace o tom, jak uložit privátní klíč do kontejneru klíčů, najdete v tématu [Postupy: ukládání asymetrických klíčů v kontejneru klíčů](how-to-store-asymmetric-keys-in-a-key-container.md).  
  
 Následující příklad kódu vytvoří novou instanci třídy **RSACryptoServiceProvider** , vytvoří dvojici veřejného a privátního klíče a uloží informace o veřejném klíči do struktury **RSAParameters** .  
  
```vb  
'Generate a public/private key pair.  
Dim rsa as RSACryptoServiceProvider = new RSACryptoServiceProvider()  
'Save the public key information to an RSAParameters structure.  
Dim rsaKeyInfo As RSAParameters = rsa.ExportParameters(false)  
```  
  
```csharp  
//Generate a public/private key pair.  
RSACryptoServiceProvider rsa = new RSACryptoServiceProvider();  
//Save the public key information to an RSAParameters structure.  
RSAParameters rsaKeyInfo = rsa.ExportParameters(false);  
```  
  
## <a name="see-also"></a>Viz také

- [Šifrování dat](encrypting-data.md)
- [Dešifrování dat](decrypting-data.md)
- [Kryptografické služby](cryptographic-services.md)
- [Postupy: Uložení asymetrického klíče v kontejneru klíčů](how-to-store-asymmetric-keys-in-a-key-container.md)
