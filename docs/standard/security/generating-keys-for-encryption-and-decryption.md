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
# <a name="generating-keys-for-encryption-and-decryption"></a><span data-ttu-id="d868a-103">Generování klíčů pro šifrování a dešifrování</span><span class="sxs-lookup"><span data-stu-id="d868a-103">Generating Keys for Encryption and Decryption</span></span>
<span data-ttu-id="d868a-104">Vytváření a správa klíčů je důležitou součástí procesu šifrování.</span><span class="sxs-lookup"><span data-stu-id="d868a-104">Creating and managing keys is an important part of the cryptographic process.</span></span> <span data-ttu-id="d868a-105">Symetrické algoritmy vyžadují vytvoření klíče a inicializačního vektoru (IV).</span><span class="sxs-lookup"><span data-stu-id="d868a-105">Symmetric algorithms require the creation of a key and an initialization vector (IV).</span></span> <span data-ttu-id="d868a-106">Klíč musí být udržen v tajnosti před kýmkoli, kdo by neměl data dešifrovat.</span><span class="sxs-lookup"><span data-stu-id="d868a-106">The key must be kept secret from anyone who should not decrypt your data.</span></span> <span data-ttu-id="d868a-107">Vektor IV nemusí být tajný, ale měli byste jej pro jednotlivé relace změnit.</span><span class="sxs-lookup"><span data-stu-id="d868a-107">The IV does not have to be secret, but should be changed for each session.</span></span> <span data-ttu-id="d868a-108">Asymetrické algoritmy vyžadují vytvoření veřejného klíče a soukromého klíče.</span><span class="sxs-lookup"><span data-stu-id="d868a-108">Asymmetric algorithms require the creation of a public key and a private key.</span></span> <span data-ttu-id="d868a-109">Veřejný klíč se může zveřejnit všem uživatelům, zatímco soukromý klíč smí být znám pouze osobě, která bude dešifrovat data zašifrovaná pomocí veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="d868a-109">The public key can be made public to anyone, while the private key must known only by the party who will decrypt the data encrypted with the public key.</span></span> <span data-ttu-id="d868a-110">V této části je popsán způsob vytváření a správy klíčů pro symetrické i asymetrické algoritmy.</span><span class="sxs-lookup"><span data-stu-id="d868a-110">This section describes how to generate and manage keys for both symmetric and asymmetric algorithms.</span></span>  
  
## <a name="symmetric-keys"></a><span data-ttu-id="d868a-111">Symetrické klíče</span><span class="sxs-lookup"><span data-stu-id="d868a-111">Symmetric Keys</span></span>  
 <span data-ttu-id="d868a-112">Třídy symetrického šifrování dodávané rozhraním .NET vyžadují klíč a nový inicializační vektor (IV) pro šifrování a dešifrování dat.</span><span class="sxs-lookup"><span data-stu-id="d868a-112">The symmetric encryption classes supplied by .NET require a key and a new initialization vector (IV) to encrypt and decrypt data.</span></span> <span data-ttu-id="d868a-113">Kdykoli vytvoříte novou instanci jedné ze spravovaných symetrických kryptografických tříd pomocí metody bez parametrů `Create()` , automaticky se vytvoří nový klíč a IV.</span><span class="sxs-lookup"><span data-stu-id="d868a-113">Whenever you create a new instance of one of the managed symmetric cryptographic classes using the parameterless `Create()` method, a new key and IV are automatically created.</span></span> <span data-ttu-id="d868a-114">Jakákoli osoba s oprávněním k dešifrování dat musí mít stejný klíč a vektor IV a použít stejný algoritmus.</span><span class="sxs-lookup"><span data-stu-id="d868a-114">Anyone that you allow to decrypt your data must possess the same key and IV and use the same algorithm.</span></span> <span data-ttu-id="d868a-115">Obecně lze říci, že nový klíč a vektor IV by měly být vytvořeny pro každou relaci a klíč ani vektor IV by neměly být ukládány pro používání v pozdější relaci.</span><span class="sxs-lookup"><span data-stu-id="d868a-115">Generally, a new key and IV should be created for every session, and neither the key nor IV should be stored for use in a later session.</span></span>  
  
 <span data-ttu-id="d868a-116">Ke sdělení symetrického klíče a vektoru IV vzdálené straně je obvykle třeba zašifrovat symetrický klíč pomocí asymetrického šifrování.</span><span class="sxs-lookup"><span data-stu-id="d868a-116">To communicate a symmetric key and IV to a remote party, you would usually encrypt the symmetric key by using asymmetric encryption.</span></span> <span data-ttu-id="d868a-117">Odesílání klíče v nezabezpečené síti bez šifrování je velmi nebezpečné, jelikož jakákoli osoba, která klíč a vektor IV zachytí, může data dešifrovat.</span><span class="sxs-lookup"><span data-stu-id="d868a-117">Sending the key across an insecure network without encrypting it is unsafe, because anyone who intercepts the key and IV can then decrypt your data.</span></span>  
  
 <span data-ttu-id="d868a-118">Následující příklad ukazuje vytvoření nové instance výchozí třídy implementace pro <xref:System.Security.Cryptography.Aes> algoritmus.</span><span class="sxs-lookup"><span data-stu-id="d868a-118">The following example shows the creation of a new instance of the default implementation class for the <xref:System.Security.Cryptography.Aes> algorithm.</span></span>  
  
```vb  
Dim aes As Aes = Aes.Create()  
```  
  
```csharp  
Aes aes = Aes.Create();  
```  
  
 <span data-ttu-id="d868a-119">Když se spustí předchozí kód, vygeneruje se nový klíč a IV a umístí se do vlastností **Key** a **IV** v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="d868a-119">When the previous code is executed, a new key and IV are generated and placed in the **Key** and **IV** properties, respectively.</span></span>  
  
 <span data-ttu-id="d868a-120">Občas bude pravděpodobně nutné generovat více klíčů.</span><span class="sxs-lookup"><span data-stu-id="d868a-120">Sometimes you might need to generate multiple keys.</span></span> <span data-ttu-id="d868a-121">V této situaci můžete vytvořit novou instanci třídy, která implementuje symetrický algoritmus, a pak vytvořit nový klíč a IV voláním metod **GenerateKey** a **GenerateIV** .</span><span class="sxs-lookup"><span data-stu-id="d868a-121">In this situation, you can create a new instance of a class that implements a symmetric algorithm and then create a new key and IV by calling the **GenerateKey** and **GenerateIV** methods.</span></span> <span data-ttu-id="d868a-122">Následující příklad kódu ukazuje, jak vytvořit nové klíče a Ideographic po provedení nové instance symetrické kryptografické třídy.</span><span class="sxs-lookup"><span data-stu-id="d868a-122">The following code example illustrates how to create new keys and IVs after a new instance of the symmetric cryptographic class has been made.</span></span>  
  
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
  
 <span data-ttu-id="d868a-123">Když je proveden předchozí kód, klíč a IV jsou generovány při vytvoření nové instance **AES** .</span><span class="sxs-lookup"><span data-stu-id="d868a-123">When the preceding code is executed, a key and IV are generated when the new instance of **Aes** is made.</span></span> <span data-ttu-id="d868a-124">Při volání metod **GenerateKey** a **GenerateIV** se vytvoří další klíč a IV.</span><span class="sxs-lookup"><span data-stu-id="d868a-124">Another key and IV are created when the **GenerateKey** and **GenerateIV** methods are called.</span></span>
  
## <a name="asymmetric-keys"></a><span data-ttu-id="d868a-125">Asymetrické klíče</span><span class="sxs-lookup"><span data-stu-id="d868a-125">Asymmetric Keys</span></span>

 <span data-ttu-id="d868a-126">Rozhraní .NET poskytuje <xref:System.Security.Cryptography.RSA> třídu pro asymetrické šifrování.</span><span class="sxs-lookup"><span data-stu-id="d868a-126">.NET provides the <xref:System.Security.Cryptography.RSA> class for asymmetric encryption.</span></span> <span data-ttu-id="d868a-127">Tato třída vytvoří pár veřejného a privátního klíče, pokud použijete metodu bez parametrů `Create()` k vytvoření nové instance.</span><span class="sxs-lookup"><span data-stu-id="d868a-127">This class creates a public/private key pair when you use the parameterless `Create()` method to create a new instance.</span></span> <span data-ttu-id="d868a-128">Asymetrické klíče mohou být buď uloženy pro použití ve více relacích, nebo generovány pouze pro jednu relaci.</span><span class="sxs-lookup"><span data-stu-id="d868a-128">Asymmetric keys can be either stored for use in multiple sessions or generated for one session only.</span></span> <span data-ttu-id="d868a-129">Zatímco veřejný klíč může být zpřístupněn veřejně, soukromý klíč by měl být přísně chráněný.</span><span class="sxs-lookup"><span data-stu-id="d868a-129">While the public key can be made generally available, the private key should be closely guarded.</span></span>  
  
 <span data-ttu-id="d868a-130">Pár veřejného/soukromého klíče je generován při každém vytvoření nové instance třídy asymetrického algoritmu.</span><span class="sxs-lookup"><span data-stu-id="d868a-130">A public/private key pair is generated whenever a new instance of an asymmetric algorithm class is created.</span></span> <span data-ttu-id="d868a-131">Po vytvoření nové instance třídy mohou být informace o klíči extrahovány pomocí <xref:System.Security.Cryptography.RSA.ExportParameters%2A> metody, která vrací <xref:System.Security.Cryptography.RSAParameters> strukturu, která obsahuje informace o klíči.</span><span class="sxs-lookup"><span data-stu-id="d868a-131">After a new instance of the class is created, the key information can be extracted using the <xref:System.Security.Cryptography.RSA.ExportParameters%2A> method, which returns an <xref:System.Security.Cryptography.RSAParameters> structure that holds the key information.</span></span> <span data-ttu-id="d868a-132">Metoda přijímá logickou hodnotu, která označuje, jestli se mají vracet jenom informace o veřejném klíči, nebo jestli se mají vracet informace o veřejném klíči i s privátním klíčem.</span><span class="sxs-lookup"><span data-stu-id="d868a-132">The method accepts a Boolean value that indicates whether to return only the public key information or to return both the public-key and the private-key information.</span></span>

<span data-ttu-id="d868a-133">Existují také jiné metody, které umožňují extrahování klíčových informací, například:</span><span class="sxs-lookup"><span data-stu-id="d868a-133">There are also other methods that let you extract key information, such as:</span></span>

* <xref:System.Security.Cryptography.RSA.ExportRSAPublicKey%2A?displayProperty=nameWithType>
* <xref:System.Security.Cryptography.RSA.ExportRSAPrivateKey%2A?displayProperty=nameWithType>
* <xref:System.Security.Cryptography.AsymmetricAlgorithm.ExportSubjectPublicKeyInfo%2A?displayProperty=nameWithType>
* <xref:System.Security.Cryptography.AsymmetricAlgorithm.ExportPkcs8PrivateKey%2A?displayProperty=nameWithType>
* <xref:System.Security.Cryptography.AsymmetricAlgorithm.ExportEncryptedPkcs8PrivateKey%2A?displayProperty=nameWithType>

<span data-ttu-id="d868a-134">Instance **RSA** může být inicializována na hodnotu struktury **RSAParameters** pomocí <xref:System.Security.Cryptography.RSA.ImportParameters%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="d868a-134">An **RSA** instance can be initialized to the value of an **RSAParameters** structure by using the <xref:System.Security.Cryptography.RSA.ImportParameters%2A> method.</span></span> <span data-ttu-id="d868a-135">Nebo vytvořte novou instanci pomocí <xref:System.Security.Cryptography.RSA.Create(System.Security.Cryptography.RSAParameters)?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="d868a-135">Or create a new instance by using the <xref:System.Security.Cryptography.RSA.Create(System.Security.Cryptography.RSAParameters)?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="d868a-136">Asymetrické soukromé klíče by nikdy neměly být uloženy doslovně nebo ve formátu prostého textu v místním počítači.</span><span class="sxs-lookup"><span data-stu-id="d868a-136">Asymmetric private keys should never be stored verbatim or in plain text on the local computer.</span></span> <span data-ttu-id="d868a-137">Pokud potřebujete uložit soukromý klíč, měli byste použít kontejner klíčů.</span><span class="sxs-lookup"><span data-stu-id="d868a-137">If you need to store a private key, you should use a key container.</span></span> <span data-ttu-id="d868a-138">Další informace o tom, jak uložit privátní klíč do kontejneru klíčů, naleznete v tématu [How to: Store asymetrické klíče in a Key Container](how-to-store-asymmetric-keys-in-a-key-container.md).</span><span class="sxs-lookup"><span data-stu-id="d868a-138">For more information about how to store a private key in a key container, see [How to: Store Asymmetric Keys in a Key Container](how-to-store-asymmetric-keys-in-a-key-container.md).</span></span>  
  
 <span data-ttu-id="d868a-139">Následující příklad kódu vytvoří novou instanci třídy **RSA** , vytvoří dvojici veřejného a privátního klíče a uloží informace o veřejném klíči do struktury **RSAParameters** .</span><span class="sxs-lookup"><span data-stu-id="d868a-139">The following code example creates a new instance of the **RSA** class, creating a public/private key pair, and saves the public key information to an **RSAParameters** structure.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d868a-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="d868a-140">See also</span></span>

- [<span data-ttu-id="d868a-141">Šifrování dat</span><span class="sxs-lookup"><span data-stu-id="d868a-141">Encrypting Data</span></span>](encrypting-data.md)
- [<span data-ttu-id="d868a-142">Dešifrování dat</span><span class="sxs-lookup"><span data-stu-id="d868a-142">Decrypting Data</span></span>](decrypting-data.md)
- [<span data-ttu-id="d868a-143">Šifrovací služby</span><span class="sxs-lookup"><span data-stu-id="d868a-143">Cryptographic Services</span></span>](cryptographic-services.md)
- [<span data-ttu-id="d868a-144">Postupy: Uložení asymetrického klíče v kontejneru klíčů</span><span class="sxs-lookup"><span data-stu-id="d868a-144">How to: Store Asymmetric Keys in a Key Container</span></span>](how-to-store-asymmetric-keys-in-a-key-container.md)
- [<span data-ttu-id="d868a-145">Kryptografie pro různé platformy</span><span class="sxs-lookup"><span data-stu-id="d868a-145">Cross-Platform Cryptography</span></span>](cross-platform-cryptography.md)
- [<span data-ttu-id="d868a-146">Ochrana dat ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="d868a-146">ASP.NET Core Data Protection</span></span>](/aspnet/core/security/data-protection/introduction)
