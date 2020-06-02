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
# <a name="generating-keys-for-encryption-and-decryption"></a><span data-ttu-id="179e7-102">Generování klíčů pro šifrování a dešifrování</span><span class="sxs-lookup"><span data-stu-id="179e7-102">Generating Keys for Encryption and Decryption</span></span>
<span data-ttu-id="179e7-103">Vytváření a správa klíčů je důležitou součástí procesu šifrování.</span><span class="sxs-lookup"><span data-stu-id="179e7-103">Creating and managing keys is an important part of the cryptographic process.</span></span> <span data-ttu-id="179e7-104">Symetrické algoritmy vyžadují vytvoření klíče a inicializačního vektoru (IV).</span><span class="sxs-lookup"><span data-stu-id="179e7-104">Symmetric algorithms require the creation of a key and an initialization vector (IV).</span></span> <span data-ttu-id="179e7-105">Klíč musí být udržen v tajnosti před kýmkoli, kdo by neměl data dešifrovat.</span><span class="sxs-lookup"><span data-stu-id="179e7-105">The key must be kept secret from anyone who should not decrypt your data.</span></span> <span data-ttu-id="179e7-106">Vektor IV nemusí být tajný, ale měli byste jej pro jednotlivé relace změnit.</span><span class="sxs-lookup"><span data-stu-id="179e7-106">The IV does not have to be secret, but should be changed for each session.</span></span> <span data-ttu-id="179e7-107">Asymetrické algoritmy vyžadují vytvoření veřejného klíče a soukromého klíče.</span><span class="sxs-lookup"><span data-stu-id="179e7-107">Asymmetric algorithms require the creation of a public key and a private key.</span></span> <span data-ttu-id="179e7-108">Veřejný klíč se může zveřejnit všem uživatelům, zatímco soukromý klíč smí být znám pouze osobě, která bude dešifrovat data zašifrovaná pomocí veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="179e7-108">The public key can be made public to anyone, while the private key must known only by the party who will decrypt the data encrypted with the public key.</span></span> <span data-ttu-id="179e7-109">V této části je popsán způsob vytváření a správy klíčů pro symetrické i asymetrické algoritmy.</span><span class="sxs-lookup"><span data-stu-id="179e7-109">This section describes how to generate and manage keys for both symmetric and asymmetric algorithms.</span></span>  
  
## <a name="symmetric-keys"></a><span data-ttu-id="179e7-110">Symetrické klíče</span><span class="sxs-lookup"><span data-stu-id="179e7-110">Symmetric Keys</span></span>  
 <span data-ttu-id="179e7-111">Třídy pro symetrické šifrování poskytované rozhraním .NET Framework vyžadují klíč a nový inicializační vektor (IV) k šifrování a dešifrování dat.</span><span class="sxs-lookup"><span data-stu-id="179e7-111">The symmetric encryption classes supplied by the .NET Framework require a key and a new initialization vector (IV) to encrypt and decrypt data.</span></span> <span data-ttu-id="179e7-112">Kdykoli vytvoříte novou instanci jedné ze spravovaných symetrických kryptografických tříd pomocí konstruktoru bez parametrů, automaticky se vytvoří nový klíč a IV.</span><span class="sxs-lookup"><span data-stu-id="179e7-112">Whenever you create a new instance of one of the managed symmetric cryptographic classes using the parameterless constructor, a new key and IV are automatically created.</span></span> <span data-ttu-id="179e7-113">Jakákoli osoba s oprávněním k dešifrování dat musí mít stejný klíč a vektor IV a použít stejný algoritmus.</span><span class="sxs-lookup"><span data-stu-id="179e7-113">Anyone that you allow to decrypt your data must possess the same key and IV and use the same algorithm.</span></span> <span data-ttu-id="179e7-114">Obecně lze říci, že nový klíč a vektor IV by měly být vytvořeny pro každou relaci a klíč ani vektor IV by neměly být ukládány pro používání v pozdější relaci.</span><span class="sxs-lookup"><span data-stu-id="179e7-114">Generally, a new key and IV should be created for every session, and neither the key nor IV should be stored for use in a later session.</span></span>  
  
 <span data-ttu-id="179e7-115">Ke sdělení symetrického klíče a vektoru IV vzdálené straně je obvykle třeba zašifrovat symetrický klíč pomocí asymetrického šifrování.</span><span class="sxs-lookup"><span data-stu-id="179e7-115">To communicate a symmetric key and IV to a remote party, you would usually encrypt the symmetric key by using asymmetric encryption.</span></span> <span data-ttu-id="179e7-116">Odesílání klíče v nezabezpečené síti bez šifrování je velmi nebezpečné, jelikož jakákoli osoba, která klíč a vektor IV zachytí, může data dešifrovat.</span><span class="sxs-lookup"><span data-stu-id="179e7-116">Sending the key across an insecure network without encrypting it is unsafe, because anyone who intercepts the key and IV can then decrypt your data.</span></span> <span data-ttu-id="179e7-117">Další informace o výměně dat pomocí šifrování najdete v tématu [Vytvoření kryptografického schématu](creating-a-cryptographic-scheme.md).</span><span class="sxs-lookup"><span data-stu-id="179e7-117">For more information about exchanging data by using encryption, see [Creating a Cryptographic Scheme](creating-a-cryptographic-scheme.md).</span></span>  
  
 <span data-ttu-id="179e7-118">Následující příklad znázorňuje vytvoření nové instance třídy <xref:System.Security.Cryptography.TripleDESCryptoServiceProvider>, která implementuje algoritmus TripleDES.</span><span class="sxs-lookup"><span data-stu-id="179e7-118">The following example shows the creation of a new instance of the <xref:System.Security.Cryptography.TripleDESCryptoServiceProvider> class that implements the TripleDES algorithm.</span></span>  
  
```vb  
Dim tdes As TripleDESCryptoServiceProvider = new TripleDESCryptoServiceProvider()  
```  
  
```csharp  
TripleDESCryptoServiceProvider tdes = new TripleDESCryptoServiceProvider();  
```  
  
 <span data-ttu-id="179e7-119">Když se spustí předchozí kód, vygeneruje se nový klíč a IV a umístí se do vlastností **Key** a **IV** v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="179e7-119">When the previous code is executed, a new key and IV are generated and placed in the **Key** and **IV** properties, respectively.</span></span>  
  
 <span data-ttu-id="179e7-120">Občas bude pravděpodobně nutné generovat více klíčů.</span><span class="sxs-lookup"><span data-stu-id="179e7-120">Sometimes you might need to generate multiple keys.</span></span> <span data-ttu-id="179e7-121">V této situaci můžete vytvořit novou instanci třídy, která implementuje symetrický algoritmus, a pak vytvořit nový klíč a IV voláním metod **GenerateKey** a **GenerateIV** .</span><span class="sxs-lookup"><span data-stu-id="179e7-121">In this situation, you can create a new instance of a class that implements a symmetric algorithm and then create a new key and IV by calling the **GenerateKey** and **GenerateIV** methods.</span></span> <span data-ttu-id="179e7-122">Následující příklad kódu ukazuje, jak vytvořit nové klíče a Ideographic po provedení nové instance symetrické kryptografické třídy.</span><span class="sxs-lookup"><span data-stu-id="179e7-122">The following code example illustrates how to create new keys and IVs after a new instance of the symmetric cryptographic class has been made.</span></span>  
  
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
  
 <span data-ttu-id="179e7-123">Když je proveden předchozí kód, klíč a IV jsou generovány při vytvoření nové instance **TripleDESCryptoServiceProvider** .</span><span class="sxs-lookup"><span data-stu-id="179e7-123">When the previous code is executed, a key and IV are generated when the new instance of **TripleDESCryptoServiceProvider** is made.</span></span> <span data-ttu-id="179e7-124">Při volání metod **GenerateKey** a **GenerateIV** se vytvoří další klíč a IV.</span><span class="sxs-lookup"><span data-stu-id="179e7-124">Another key and IV are created when the **GenerateKey** and **GenerateIV** methods are called.</span></span>  
  
## <a name="asymmetric-keys"></a><span data-ttu-id="179e7-125">Asymetrické klíče</span><span class="sxs-lookup"><span data-stu-id="179e7-125">Asymmetric Keys</span></span>  
 <span data-ttu-id="179e7-126">Rozhraní .NET Framework poskytuje třídy <xref:System.Security.Cryptography.RSACryptoServiceProvider> a <xref:System.Security.Cryptography.DSACryptoServiceProvider> pro asymetrické šifrování.</span><span class="sxs-lookup"><span data-stu-id="179e7-126">The .NET Framework provides the <xref:System.Security.Cryptography.RSACryptoServiceProvider> and <xref:System.Security.Cryptography.DSACryptoServiceProvider> classes for asymmetric encryption.</span></span> <span data-ttu-id="179e7-127">Tyto třídy vytvoří pár veřejného a privátního klíče, pokud použijete konstruktor bez parametrů k vytvoření nové instance.</span><span class="sxs-lookup"><span data-stu-id="179e7-127">These classes create a public/private key pair when you use the parameterless constructor to create a new instance.</span></span> <span data-ttu-id="179e7-128">Asymetrické klíče mohou být buď uloženy pro použití ve více relacích, nebo generovány pouze pro jednu relaci.</span><span class="sxs-lookup"><span data-stu-id="179e7-128">Asymmetric keys can be either stored for use in multiple sessions or generated for one session only.</span></span> <span data-ttu-id="179e7-129">Zatímco veřejný klíč může být zpřístupněn veřejně, soukromý klíč by měl být přísně chráněný.</span><span class="sxs-lookup"><span data-stu-id="179e7-129">While the public key can be made generally available, the private key should be closely guarded.</span></span>  
  
 <span data-ttu-id="179e7-130">Pár veřejného/soukromého klíče je generován při každém vytvoření nové instance třídy asymetrického algoritmu.</span><span class="sxs-lookup"><span data-stu-id="179e7-130">A public/private key pair is generated whenever a new instance of an asymmetric algorithm class is created.</span></span> <span data-ttu-id="179e7-131">Po vytvoření nové instance třídy může být informace o klíči extrahována pomocí jedné ze dvou metod:</span><span class="sxs-lookup"><span data-stu-id="179e7-131">After a new instance of the class is created, the key information can be extracted using one of two methods:</span></span>  
  
- <span data-ttu-id="179e7-132"><xref:System.Security.Cryptography.RSA.ToXmlString%2A>Metoda, která vrátí reprezentaci informací o klíči XML.</span><span class="sxs-lookup"><span data-stu-id="179e7-132">The <xref:System.Security.Cryptography.RSA.ToXmlString%2A> method, which returns an XML representation of the key information.</span></span>  
  
- <span data-ttu-id="179e7-133">Metodou <xref:System.Security.Cryptography.RSACryptoServiceProvider.ExportParameters%2A>, která vrátí strukturu <xref:System.Security.Cryptography.RSAParameters> s informacemi o klíči.</span><span class="sxs-lookup"><span data-stu-id="179e7-133">The <xref:System.Security.Cryptography.RSACryptoServiceProvider.ExportParameters%2A> method, which returns an <xref:System.Security.Cryptography.RSAParameters> structure that holds the key information.</span></span>  
  
 <span data-ttu-id="179e7-134">Obě metody přijímají logickou hodnotu, která označuje, zda vrátit informace pouze o veřejném klíči nebo zda vrátit také informace o veřejném klíči a soukromém klíči.</span><span class="sxs-lookup"><span data-stu-id="179e7-134">Both methods accept a Boolean value that indicates whether to return only the public key information or to return both the public-key and the private-key information.</span></span> <span data-ttu-id="179e7-135">Třída **RSACryptoServiceProvider** může být inicializována na hodnotu struktury **RSAParameters** pomocí <xref:System.Security.Cryptography.RSACryptoServiceProvider.ImportParameters%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="179e7-135">An **RSACryptoServiceProvider** class can be initialized to the value of an **RSAParameters** structure by using the <xref:System.Security.Cryptography.RSACryptoServiceProvider.ImportParameters%2A> method.</span></span>  
  
 <span data-ttu-id="179e7-136">Asymetrické soukromé klíče by nikdy neměly být uloženy doslovně nebo ve formátu prostého textu v místním počítači.</span><span class="sxs-lookup"><span data-stu-id="179e7-136">Asymmetric private keys should never be stored verbatim or in plain text on the local computer.</span></span> <span data-ttu-id="179e7-137">Pokud potřebujete uložit soukromý klíč, měli byste použít kontejner klíčů.</span><span class="sxs-lookup"><span data-stu-id="179e7-137">If you need to store a private key, you should use a key container.</span></span> <span data-ttu-id="179e7-138">Další informace o tom, jak uložit privátní klíč do kontejneru klíčů, najdete v tématu [Postupy: ukládání asymetrických klíčů v kontejneru klíčů](how-to-store-asymmetric-keys-in-a-key-container.md).</span><span class="sxs-lookup"><span data-stu-id="179e7-138">For more on how to store a private key in a key container, see [How to: Store Asymmetric Keys in a Key Container](how-to-store-asymmetric-keys-in-a-key-container.md).</span></span>  
  
 <span data-ttu-id="179e7-139">Následující příklad kódu vytvoří novou instanci třídy **RSACryptoServiceProvider** , vytvoří dvojici veřejného a privátního klíče a uloží informace o veřejném klíči do struktury **RSAParameters** .</span><span class="sxs-lookup"><span data-stu-id="179e7-139">The following code example creates a new instance of the **RSACryptoServiceProvider** class, creating a public/private key pair, and saves the public key information to an **RSAParameters** structure.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="179e7-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="179e7-140">See also</span></span>

- [<span data-ttu-id="179e7-141">Šifrování dat</span><span class="sxs-lookup"><span data-stu-id="179e7-141">Encrypting Data</span></span>](encrypting-data.md)
- [<span data-ttu-id="179e7-142">Dešifrování dat</span><span class="sxs-lookup"><span data-stu-id="179e7-142">Decrypting Data</span></span>](decrypting-data.md)
- [<span data-ttu-id="179e7-143">Kryptografické služby</span><span class="sxs-lookup"><span data-stu-id="179e7-143">Cryptographic Services</span></span>](cryptographic-services.md)
- [<span data-ttu-id="179e7-144">Postupy: Uložení asymetrického klíče v kontejneru klíčů</span><span class="sxs-lookup"><span data-stu-id="179e7-144">How to: Store Asymmetric Keys in a Key Container</span></span>](how-to-store-asymmetric-keys-in-a-key-container.md)
