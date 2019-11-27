---
title: Šifrování a dešifrování řetězců
ms.date: 07/20/2015
helpviewer_keywords:
- encryption [Visual Basic], strings
- strings [Visual Basic], encrypting
- decryption [Visual Basic], strings
- strings [Visual Basic], decrypting
ms.assetid: 1f51e40a-2f88-43e2-a83e-28a0b5c0d6fd
ms.openlocfilehash: 36e405c7362993471d3e6da8e319bccb854e1026
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343587"
---
# <a name="walkthrough-encrypting-and-decrypting-strings-in-visual-basic"></a><span data-ttu-id="91a5d-102">Návod: Šifrování a dešifrování řetězců v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="91a5d-102">Walkthrough: Encrypting and Decrypting Strings in Visual Basic</span></span>
<span data-ttu-id="91a5d-103">V tomto návodu se dozvíte, jak používat třídu <xref:System.Security.Cryptography.DESCryptoServiceProvider> k šifrování a dešifrování řetězců pomocí verze zprostředkovatele kryptografických služeb (CSP) algoritmu Triple Data Encryption Standard (<xref:System.Security.Cryptography.TripleDES>).</span><span class="sxs-lookup"><span data-stu-id="91a5d-103">This walkthrough shows you how to use the <xref:System.Security.Cryptography.DESCryptoServiceProvider> class to encrypt and decrypt strings using the cryptographic service provider (CSP) version of the Triple Data Encryption Standard (<xref:System.Security.Cryptography.TripleDES>) algorithm.</span></span> <span data-ttu-id="91a5d-104">Prvním krokem je vytvořit jednoduchou obálkovou třídu, která zapouzdřuje algoritmus 3DES a uloží šifrovaná data jako řetězec s kódováním Base-64.</span><span class="sxs-lookup"><span data-stu-id="91a5d-104">The first step is to create a simple wrapper class that encapsulates the 3DES algorithm and stores the encrypted data as a base-64 encoded string.</span></span> <span data-ttu-id="91a5d-105">Tato obálka pak slouží k bezpečnému ukládání privátních uživatelských dat do veřejně přístupného textového souboru.</span><span class="sxs-lookup"><span data-stu-id="91a5d-105">Then, that wrapper is used to securely store private user data in a publicly accessible text file.</span></span>  
  
 <span data-ttu-id="91a5d-106">Šifrování můžete použít k ochraně uživatelských tajných klíčů (například hesel) a k zpřístupnění přihlašovacích údajů neautorizovanými uživateli.</span><span class="sxs-lookup"><span data-stu-id="91a5d-106">You can use encryption to protect user secrets (for example, passwords) and to make credentials unreadable by unauthorized users.</span></span> <span data-ttu-id="91a5d-107">To může chránit identitu oprávněného uživatele proti krádeži, která chrání prostředky uživatele a zajišťuje Neodmítnutí.</span><span class="sxs-lookup"><span data-stu-id="91a5d-107">This can protect an authorized user's identity from being stolen, which protects the user's assets and provides non-repudiation.</span></span> <span data-ttu-id="91a5d-108">Šifrování může také chránit data uživatele před přístupem neautorizovaných uživatelů.</span><span class="sxs-lookup"><span data-stu-id="91a5d-108">Encryption can also protect a user's data from being accessed by unauthorized users.</span></span>  
  
 <span data-ttu-id="91a5d-109">Další informace najdete v tématu [kryptografické služby](../../../../standard/security/cryptographic-services.md).</span><span class="sxs-lookup"><span data-stu-id="91a5d-109">For more information, see [Cryptographic Services](../../../../standard/security/cryptographic-services.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="91a5d-110">Rozhraní Rijndael (nyní označované jako standard AES (Advanced Encryption Standard) [AES]) a algoritmy 3DES (Triple Data Encryption Standard) poskytují lepší zabezpečení než algoritmus DES, protože jsou výpočty mnohem náročné.</span><span class="sxs-lookup"><span data-stu-id="91a5d-110">The Rijndael (now referred to as Advanced Encryption Standard [AES]) and Triple Data Encryption Standard (3DES) algorithms provide greater security than DES because they are more computationally intensive.</span></span> <span data-ttu-id="91a5d-111">Další informace naleznete v tématu <xref:System.Security.Cryptography.DES> a <xref:System.Security.Cryptography.Rijndael>.</span><span class="sxs-lookup"><span data-stu-id="91a5d-111">For more information, see <xref:System.Security.Cryptography.DES> and <xref:System.Security.Cryptography.Rijndael>.</span></span>  
  
### <a name="to-create-the-encryption-wrapper"></a><span data-ttu-id="91a5d-112">Vytvoření obálky pro šifrování</span><span class="sxs-lookup"><span data-stu-id="91a5d-112">To create the encryption wrapper</span></span>  
  
1. <span data-ttu-id="91a5d-113">Vytvořte třídu `Simple3Des` pro zapouzdření šifrovacích a dešifrovacích metod.</span><span class="sxs-lookup"><span data-stu-id="91a5d-113">Create the `Simple3Des` class to encapsulate the encryption and decryption methods.</span></span>  
  
     [!code-vb[VbVbalrStrings#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#38)]  
  
2. <span data-ttu-id="91a5d-114">Přidejte import oboru názvů kryptografie na začátek souboru, který obsahuje třídu `Simple3Des`.</span><span class="sxs-lookup"><span data-stu-id="91a5d-114">Add an import of the cryptography namespace to the start of the file that contains the `Simple3Des` class.</span></span>  
  
     [!code-vb[VbVbalrStrings#77](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#77)]  
  
3. <span data-ttu-id="91a5d-115">Ve třídě `Simple3Des` přidejte soukromé pole pro uložení poskytovatele kryptografických služeb 3DES.</span><span class="sxs-lookup"><span data-stu-id="91a5d-115">In the `Simple3Des` class, add a private field to store the 3DES cryptographic service provider.</span></span>  
  
     [!code-vb[VbVbalrStrings#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#39)]  
  
4. <span data-ttu-id="91a5d-116">Přidejte soukromou metodu, která vytvoří pole bajtů o zadané délce z hodnoty hash zadaného klíče.</span><span class="sxs-lookup"><span data-stu-id="91a5d-116">Add a private method that creates a byte array of a specified length from the hash of the specified key.</span></span>  
  
     [!code-vb[VbVbalrStrings#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#41)]  
  
5. <span data-ttu-id="91a5d-117">Přidejte konstruktor pro inicializaci zprostředkovatele kryptografických služeb 3DES.</span><span class="sxs-lookup"><span data-stu-id="91a5d-117">Add a constructor to initialize the 3DES cryptographic service provider.</span></span>  
  
     <span data-ttu-id="91a5d-118">Parametr `key` řídí metody `EncryptData` a `DecryptData`.</span><span class="sxs-lookup"><span data-stu-id="91a5d-118">The `key` parameter controls the `EncryptData` and `DecryptData` methods.</span></span>  
  
     [!code-vb[VbVbalrStrings#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#40)]  
  
6. <span data-ttu-id="91a5d-119">Přidejte veřejnou metodu, která šifruje řetězec.</span><span class="sxs-lookup"><span data-stu-id="91a5d-119">Add a public method that encrypts a string.</span></span>  
  
     [!code-vb[VbVbalrStrings#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#42)]  
  
7. <span data-ttu-id="91a5d-120">Přidejte veřejnou metodu, která dešifruje řetězec.</span><span class="sxs-lookup"><span data-stu-id="91a5d-120">Add a public method that decrypts a string.</span></span>  
  
     [!code-vb[VbVbalrStrings#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#43)]  
  
     <span data-ttu-id="91a5d-121">Obálková třída se teď dá použít k ochraně prostředků uživatele.</span><span class="sxs-lookup"><span data-stu-id="91a5d-121">The wrapper class can now be used to protect user assets.</span></span> <span data-ttu-id="91a5d-122">V tomto příkladu se používá k bezpečnému ukládání privátních uživatelských dat do veřejně přístupného textového souboru.</span><span class="sxs-lookup"><span data-stu-id="91a5d-122">In this example, it is used to securely store private user data in a publicly accessible text file.</span></span>  
  
### <a name="to-test-the-encryption-wrapper"></a><span data-ttu-id="91a5d-123">Otestování obálky šifrování</span><span class="sxs-lookup"><span data-stu-id="91a5d-123">To test the encryption wrapper</span></span>  
  
1. <span data-ttu-id="91a5d-124">V samostatné třídě přidejte metodu, která používá `EncryptData` metodu obálky k zašifrování řetězce a zapište ho do složky Dokumenty uživatele.</span><span class="sxs-lookup"><span data-stu-id="91a5d-124">In a separate class, add a method that uses the wrapper's `EncryptData` method to encrypt a string and write it to the user's My Documents folder.</span></span>  
  
     [!code-vb[VbVbalrStrings#78](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#78)]  
  
2. <span data-ttu-id="91a5d-125">Přidejte metodu, která přečte zašifrovaný řetězec ze složky dokumenty daného uživatele a dešifruje řetězec pomocí `DecryptData` metody obálky.</span><span class="sxs-lookup"><span data-stu-id="91a5d-125">Add a method that reads the encrypted string from the user's My Documents folder and decrypts the string with the wrapper's `DecryptData` method.</span></span>  
  
     [!code-vb[VbVbalrStrings#79](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#79)]  
  
3. <span data-ttu-id="91a5d-126">Přidejte kód uživatelského rozhraní pro volání metod `TestEncoding` a `TestDecoding`.</span><span class="sxs-lookup"><span data-stu-id="91a5d-126">Add user interface code to call the `TestEncoding` and `TestDecoding` methods.</span></span>  
  
4. <span data-ttu-id="91a5d-127">Spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="91a5d-127">Run the application.</span></span>  
  
     <span data-ttu-id="91a5d-128">Když otestujete aplikaci, Všimněte si, že nebude dešifrovat data, pokud zadáte chybné heslo.</span><span class="sxs-lookup"><span data-stu-id="91a5d-128">When you test the application, notice that it will not decrypt the data if you provide the wrong password.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91a5d-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="91a5d-129">See also</span></span>

- <xref:System.Security.Cryptography>
- <xref:System.Security.Cryptography.DESCryptoServiceProvider>
- <xref:System.Security.Cryptography.DES>
- <xref:System.Security.Cryptography.TripleDES>
- <xref:System.Security.Cryptography.Rijndael>
- [<span data-ttu-id="91a5d-130">Kryptografické služby</span><span class="sxs-lookup"><span data-stu-id="91a5d-130">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
