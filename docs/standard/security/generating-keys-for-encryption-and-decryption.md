---
title: Generování klíčů pro šifrování a dešifrování
description: Naučte se vytvářet a spravovat symetrický a asymetrický klíč pro šifrování a dešifrování v .NET.
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
ms.openlocfilehash: f8c3633d18e200037235502487d0d91d42083241
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/10/2020
ms.locfileid: "84661806"
---
# <a name="generating-keys-for-encryption-and-decryption"></a><span data-ttu-id="0f68a-103">Generování klíčů pro šifrování a dešifrování</span><span class="sxs-lookup"><span data-stu-id="0f68a-103">Generating Keys for Encryption and Decryption</span></span>
<span data-ttu-id="0f68a-104">Vytváření a správa klíčů je důležitou součástí procesu šifrování.</span><span class="sxs-lookup"><span data-stu-id="0f68a-104">Creating and managing keys is an important part of the cryptographic process.</span></span> <span data-ttu-id="0f68a-105">Symetrické algoritmy vyžadují vytvoření klíče a inicializačního vektoru (IV).</span><span class="sxs-lookup"><span data-stu-id="0f68a-105">Symmetric algorithms require the creation of a key and an initialization vector (IV).</span></span> <span data-ttu-id="0f68a-106">Klíč musí být udržen v tajnosti před kýmkoli, kdo by neměl data dešifrovat.</span><span class="sxs-lookup"><span data-stu-id="0f68a-106">The key must be kept secret from anyone who should not decrypt your data.</span></span> <span data-ttu-id="0f68a-107">Vektor IV nemusí být tajný, ale měli byste jej pro jednotlivé relace změnit.</span><span class="sxs-lookup"><span data-stu-id="0f68a-107">The IV does not have to be secret, but should be changed for each session.</span></span> <span data-ttu-id="0f68a-108">Asymetrické algoritmy vyžadují vytvoření veřejného klíče a soukromého klíče.</span><span class="sxs-lookup"><span data-stu-id="0f68a-108">Asymmetric algorithms require the creation of a public key and a private key.</span></span> <span data-ttu-id="0f68a-109">Veřejný klíč se může zveřejnit všem uživatelům, zatímco soukromý klíč smí být znám pouze osobě, která bude dešifrovat data zašifrovaná pomocí veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="0f68a-109">The public key can be made public to anyone, while the private key must known only by the party who will decrypt the data encrypted with the public key.</span></span> <span data-ttu-id="0f68a-110">V této části je popsán způsob vytváření a správy klíčů pro symetrické i asymetrické algoritmy.</span><span class="sxs-lookup"><span data-stu-id="0f68a-110">This section describes how to generate and manage keys for both symmetric and asymmetric algorithms.</span></span>  
  
## <a name="symmetric-keys"></a><span data-ttu-id="0f68a-111">Symetrické klíče</span><span class="sxs-lookup"><span data-stu-id="0f68a-111">Symmetric Keys</span></span>  
 <span data-ttu-id="0f68a-112">Třídy pro symetrické šifrování poskytované rozhraním .NET Framework vyžadují klíč a nový inicializační vektor (IV) k šifrování a dešifrování dat.</span><span class="sxs-lookup"><span data-stu-id="0f68a-112">The symmetric encryption classes supplied by the .NET Framework require a key and a new initialization vector (IV) to encrypt and decrypt data.</span></span> <span data-ttu-id="0f68a-113">Kdykoli vytvoříte novou instanci jedné ze spravovaných symetrických kryptografických tříd pomocí konstruktoru bez parametrů, automaticky se vytvoří nový klíč a IV.</span><span class="sxs-lookup"><span data-stu-id="0f68a-113">Whenever you create a new instance of one of the managed symmetric cryptographic classes using the parameterless constructor, a new key and IV are automatically created.</span></span> <span data-ttu-id="0f68a-114">Jakákoli osoba s oprávněním k dešifrování dat musí mít stejný klíč a vektor IV a použít stejný algoritmus.</span><span class="sxs-lookup"><span data-stu-id="0f68a-114">Anyone that you allow to decrypt your data must possess the same key and IV and use the same algorithm.</span></span> <span data-ttu-id="0f68a-115">Obecně lze říci, že nový klíč a vektor IV by měly být vytvořeny pro každou relaci a klíč ani vektor IV by neměly být ukládány pro používání v pozdější relaci.</span><span class="sxs-lookup"><span data-stu-id="0f68a-115">Generally, a new key and IV should be created for every session, and neither the key nor IV should be stored for use in a later session.</span></span>  
  
 <span data-ttu-id="0f68a-116">Ke sdělení symetrického klíče a vektoru IV vzdálené straně je obvykle třeba zašifrovat symetrický klíč pomocí asymetrického šifrování.</span><span class="sxs-lookup"><span data-stu-id="0f68a-116">To communicate a symmetric key and IV to a remote party, you would usually encrypt the symmetric key by using asymmetric encryption.</span></span> <span data-ttu-id="0f68a-117">Odesílání klíče v nezabezpečené síti bez šifrování je velmi nebezpečné, jelikož jakákoli osoba, která klíč a vektor IV zachytí, může data dešifrovat.</span><span class="sxs-lookup"><span data-stu-id="0f68a-117">Sending the key across an insecure network without encrypting it is unsafe, because anyone who intercepts the key and IV can then decrypt your data.</span></span> <span data-ttu-id="0f68a-118">Další informace o výměně dat pomocí šifrování najdete v tématu [Vytvoření kryptografického schématu](creating-a-cryptographic-scheme.md).</span><span class="sxs-lookup"><span data-stu-id="0f68a-118">For more information about exchanging data by using encryption, see [Creating a Cryptographic Scheme](creating-a-cryptographic-scheme.md).</span></span>  
  
 <span data-ttu-id="0f68a-119">Následující příklad znázorňuje vytvoření nové instance třídy <xref:System.Security.Cryptography.TripleDESCryptoServiceProvider>, která implementuje algoritmus TripleDES.</span><span class="sxs-lookup"><span data-stu-id="0f68a-119">The following example shows the creation of a new instance of the <xref:System.Security.Cryptography.TripleDESCryptoServiceProvider> class that implements the TripleDES algorithm.</span></span>  
  
```vb  
Dim tdes As TripleDESCryptoServiceProvider = new TripleDESCryptoServiceProvider()  
```  
  
```csharp  
TripleDESCryptoServiceProvider tdes = new TripleDESCryptoServiceProvider();  
```  
  
 <span data-ttu-id="0f68a-120">Když se spustí předchozí kód, vygeneruje se nový klíč a IV a umístí se do vlastností **Key** a **IV** v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="0f68a-120">When the previous code is executed, a new key and IV are generated and placed in the **Key** and **IV** properties, respectively.</span></span>  
  
 <span data-ttu-id="0f68a-121">Občas bude pravděpodobně nutné generovat více klíčů.</span><span class="sxs-lookup"><span data-stu-id="0f68a-121">Sometimes you might need to generate multiple keys.</span></span> <span data-ttu-id="0f68a-122">V této situaci můžete vytvořit novou instanci třídy, která implementuje symetrický algoritmus, a pak vytvořit nový klíč a IV voláním metod **GenerateKey** a **GenerateIV** .</span><span class="sxs-lookup"><span data-stu-id="0f68a-122">In this situation, you can create a new instance of a class that implements a symmetric algorithm and then create a new key and IV by calling the **GenerateKey** and **GenerateIV** methods.</span></span> <span data-ttu-id="0f68a-123">Následující příklad kódu ukazuje, jak vytvořit nové klíče a Ideographic po provedení nové instance symetrické kryptografické třídy.</span><span class="sxs-lookup"><span data-stu-id="0f68a-123">The following code example illustrates how to create new keys and IVs after a new instance of the symmetric cryptographic class has been made.</span></span>  
  
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
  
 <span data-ttu-id="0f68a-124">Když je proveden předchozí kód, klíč a IV jsou generovány při vytvoření nové instance **TripleDESCryptoServiceProvider** .</span><span class="sxs-lookup"><span data-stu-id="0f68a-124">When the previous code is executed, a key and IV are generated when the new instance of **TripleDESCryptoServiceProvider** is made.</span></span> <span data-ttu-id="0f68a-125">Při volání metod **GenerateKey** a **GenerateIV** se vytvoří další klíč a IV.</span><span class="sxs-lookup"><span data-stu-id="0f68a-125">Another key and IV are created when the **GenerateKey** and **GenerateIV** methods are called.</span></span>  
  
## <a name="asymmetric-keys"></a><span data-ttu-id="0f68a-126">Asymetrické klíče</span><span class="sxs-lookup"><span data-stu-id="0f68a-126">Asymmetric Keys</span></span>  
 <span data-ttu-id="0f68a-127">Rozhraní .NET Framework poskytuje třídy <xref:System.Security.Cryptography.RSACryptoServiceProvider> a <xref:System.Security.Cryptography.DSACryptoServiceProvider> pro asymetrické šifrování.</span><span class="sxs-lookup"><span data-stu-id="0f68a-127">The .NET Framework provides the <xref:System.Security.Cryptography.RSACryptoServiceProvider> and <xref:System.Security.Cryptography.DSACryptoServiceProvider> classes for asymmetric encryption.</span></span> <span data-ttu-id="0f68a-128">Tyto třídy vytvoří pár veřejného a privátního klíče, pokud použijete konstruktor bez parametrů k vytvoření nové instance.</span><span class="sxs-lookup"><span data-stu-id="0f68a-128">These classes create a public/private key pair when you use the parameterless constructor to create a new instance.</span></span> <span data-ttu-id="0f68a-129">Asymetrické klíče mohou být buď uloženy pro použití ve více relacích, nebo generovány pouze pro jednu relaci.</span><span class="sxs-lookup"><span data-stu-id="0f68a-129">Asymmetric keys can be either stored for use in multiple sessions or generated for one session only.</span></span> <span data-ttu-id="0f68a-130">Zatímco veřejný klíč může být zpřístupněn veřejně, soukromý klíč by měl být přísně chráněný.</span><span class="sxs-lookup"><span data-stu-id="0f68a-130">While the public key can be made generally available, the private key should be closely guarded.</span></span>  
  
 <span data-ttu-id="0f68a-131">Pár veřejného/soukromého klíče je generován při každém vytvoření nové instance třídy asymetrického algoritmu.</span><span class="sxs-lookup"><span data-stu-id="0f68a-131">A public/private key pair is generated whenever a new instance of an asymmetric algorithm class is created.</span></span> <span data-ttu-id="0f68a-132">Po vytvoření nové instance třídy může být informace o klíči extrahována pomocí jedné ze dvou metod:</span><span class="sxs-lookup"><span data-stu-id="0f68a-132">After a new instance of the class is created, the key information can be extracted using one of two methods:</span></span>  
  
- <span data-ttu-id="0f68a-133"><xref:System.Security.Cryptography.RSA.ToXmlString%2A>Metoda, která vrátí reprezentaci informací o klíči XML.</span><span class="sxs-lookup"><span data-stu-id="0f68a-133">The <xref:System.Security.Cryptography.RSA.ToXmlString%2A> method, which returns an XML representation of the key information.</span></span>  
  
- <span data-ttu-id="0f68a-134">Metodou <xref:System.Security.Cryptography.RSACryptoServiceProvider.ExportParameters%2A>, která vrátí strukturu <xref:System.Security.Cryptography.RSAParameters> s informacemi o klíči.</span><span class="sxs-lookup"><span data-stu-id="0f68a-134">The <xref:System.Security.Cryptography.RSACryptoServiceProvider.ExportParameters%2A> method, which returns an <xref:System.Security.Cryptography.RSAParameters> structure that holds the key information.</span></span>  
  
 <span data-ttu-id="0f68a-135">Obě metody přijímají logickou hodnotu, která označuje, zda vrátit informace pouze o veřejném klíči nebo zda vrátit také informace o veřejném klíči a soukromém klíči.</span><span class="sxs-lookup"><span data-stu-id="0f68a-135">Both methods accept a Boolean value that indicates whether to return only the public key information or to return both the public-key and the private-key information.</span></span> <span data-ttu-id="0f68a-136">Třída **RSACryptoServiceProvider** může být inicializována na hodnotu struktury **RSAParameters** pomocí <xref:System.Security.Cryptography.RSACryptoServiceProvider.ImportParameters%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="0f68a-136">An **RSACryptoServiceProvider** class can be initialized to the value of an **RSAParameters** structure by using the <xref:System.Security.Cryptography.RSACryptoServiceProvider.ImportParameters%2A> method.</span></span>  
  
 <span data-ttu-id="0f68a-137">Asymetrické soukromé klíče by nikdy neměly být uloženy doslovně nebo ve formátu prostého textu v místním počítači.</span><span class="sxs-lookup"><span data-stu-id="0f68a-137">Asymmetric private keys should never be stored verbatim or in plain text on the local computer.</span></span> <span data-ttu-id="0f68a-138">Pokud potřebujete uložit soukromý klíč, měli byste použít kontejner klíčů.</span><span class="sxs-lookup"><span data-stu-id="0f68a-138">If you need to store a private key, you should use a key container.</span></span> <span data-ttu-id="0f68a-139">Další informace o tom, jak uložit privátní klíč do kontejneru klíčů, najdete v tématu [Postupy: ukládání asymetrických klíčů v kontejneru klíčů](how-to-store-asymmetric-keys-in-a-key-container.md).</span><span class="sxs-lookup"><span data-stu-id="0f68a-139">For more on how to store a private key in a key container, see [How to: Store Asymmetric Keys in a Key Container](how-to-store-asymmetric-keys-in-a-key-container.md).</span></span>  
  
 <span data-ttu-id="0f68a-140">Následující příklad kódu vytvoří novou instanci třídy **RSACryptoServiceProvider** , vytvoří dvojici veřejného a privátního klíče a uloží informace o veřejném klíči do struktury **RSAParameters** .</span><span class="sxs-lookup"><span data-stu-id="0f68a-140">The following code example creates a new instance of the **RSACryptoServiceProvider** class, creating a public/private key pair, and saves the public key information to an **RSAParameters** structure.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0f68a-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="0f68a-141">See also</span></span>

- [<span data-ttu-id="0f68a-142">Šifrování dat</span><span class="sxs-lookup"><span data-stu-id="0f68a-142">Encrypting Data</span></span>](encrypting-data.md)
- [<span data-ttu-id="0f68a-143">Dešifrování dat</span><span class="sxs-lookup"><span data-stu-id="0f68a-143">Decrypting Data</span></span>](decrypting-data.md)
- [<span data-ttu-id="0f68a-144">Kryptografické služby</span><span class="sxs-lookup"><span data-stu-id="0f68a-144">Cryptographic Services</span></span>](cryptographic-services.md)
- [<span data-ttu-id="0f68a-145">Postupy: Uložení asymetrického klíče v kontejneru klíčů</span><span class="sxs-lookup"><span data-stu-id="0f68a-145">How to: Store Asymmetric Keys in a Key Container</span></span>](how-to-store-asymmetric-keys-in-a-key-container.md)
