---
title: "Šifrování a dešifrování řetězců v jazyce Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- encryption [Visual Basic], strings
- strings [Visual Basic], encrypting
- decryption [Visual Basic], strings
- strings [Visual Basic], decrypting
ms.assetid: 1f51e40a-2f88-43e2-a83e-28a0b5c0d6fd
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fd9ec8e7af771db3f042e08c8ab30f6ed5832c2b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-encrypting-and-decrypting-strings-in-visual-basic"></a><span data-ttu-id="63097-102">Návod: Šifrování a dešifrování řetězců v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="63097-102">Walkthrough: Encrypting and Decrypting Strings in Visual Basic</span></span>
<span data-ttu-id="63097-103">Tento postup vám ukáže, jak používat <xref:System.Security.Cryptography.DESCryptoServiceProvider> třída k šifrování a dešifrování řetězců pomocí kryptografických služeb verze zprostředkovatele Kryptografických služeb Triple Data Encryption Standard (<xref:System.Security.Cryptography.TripleDES>) algoritmus.</span><span class="sxs-lookup"><span data-stu-id="63097-103">This walkthrough shows you how to use the <xref:System.Security.Cryptography.DESCryptoServiceProvider> class to encrypt and decrypt strings using the cryptographic service provider (CSP) version of the Triple Data Encryption Standard (<xref:System.Security.Cryptography.TripleDES>) algorithm.</span></span> <span data-ttu-id="63097-104">Prvním krokem je vytvoření jednoduché obálkovou třídu, který zapouzdřuje algoritmus 3DES a šifrovaná data uloží jako řetězec s kódováním base-64.</span><span class="sxs-lookup"><span data-stu-id="63097-104">The first step is to create a simple wrapper class that encapsulates the 3DES algorithm and stores the encrypted data as a base-64 encoded string.</span></span> <span data-ttu-id="63097-105">Potom tuto obálku slouží bezpečně uložit privátních dat uživatele do veřejně přístupné textového souboru.</span><span class="sxs-lookup"><span data-stu-id="63097-105">Then, that wrapper is used to securely store private user data in a publicly accessible text file.</span></span>  
  
 <span data-ttu-id="63097-106">Šifrování můžete použít k ochraně tajných klíčů uživatele (například hesla) a tak, aby pověření nečitelná neoprávnění uživatelé.</span><span class="sxs-lookup"><span data-stu-id="63097-106">You can use encryption to protect user secrets (for example, passwords) and to make credentials unreadable by unauthorized users.</span></span> <span data-ttu-id="63097-107">To může chránit oprávněný uživatel identity z krádeže, které chrání prostředky uživatele a poskytuje zrušení odmítnutí.</span><span class="sxs-lookup"><span data-stu-id="63097-107">This can protect an authorized user's identity from being stolen, which protects the user's assets and provides non-repudiation.</span></span> <span data-ttu-id="63097-108">Šifrování může také chránit data uživatele z Probíhá přístup neoprávnění uživatelé.</span><span class="sxs-lookup"><span data-stu-id="63097-108">Encryption can also protect a user's data from being accessed by unauthorized users.</span></span>  
  
 <span data-ttu-id="63097-109">Další informace najdete v tématu [šifrovacím službám](../../../../standard/security/cryptographic-services.md).</span><span class="sxs-lookup"><span data-stu-id="63097-109">For more information, see [Cryptographic Services](../../../../standard/security/cryptographic-services.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="63097-110">Rijndael (nyní označuje jako Advanced Encryption Standard [AES]) a Triple Data Encryption Standard (3DES) algoritmy poskytují vyšší zabezpečení než šifrování DES, protože jsou další výpočetně náročné.</span><span class="sxs-lookup"><span data-stu-id="63097-110">The Rijndael (now referred to as Advanced Encryption Standard [AES]) and Triple Data Encryption Standard (3DES) algorithms provide greater security than DES because they are more computationally intensive.</span></span> <span data-ttu-id="63097-111">Další informace naleznete v tématu <xref:System.Security.Cryptography.DES> a <xref:System.Security.Cryptography.Rijndael>.</span><span class="sxs-lookup"><span data-stu-id="63097-111">For more information, see <xref:System.Security.Cryptography.DES> and <xref:System.Security.Cryptography.Rijndael>.</span></span>  
  
### <a name="to-create-the-encryption-wrapper"></a><span data-ttu-id="63097-112">Chcete-li vytvořit obálku šifrování</span><span class="sxs-lookup"><span data-stu-id="63097-112">To create the encryption wrapper</span></span>  
  
1.  <span data-ttu-id="63097-113">Vytvořte `Simple3Des` Třída zapouzdření metody šifrování a dešifrování.</span><span class="sxs-lookup"><span data-stu-id="63097-113">Create the `Simple3Des` class to encapsulate the encryption and decryption methods.</span></span>  
  
     [!code-vb[VbVbalrStrings#38](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_1.vb)]  
  
2.  <span data-ttu-id="63097-114">Přidejte na začátek souboru, který obsahuje importu kryptografie oboru názvů `Simple3Des` třídy.</span><span class="sxs-lookup"><span data-stu-id="63097-114">Add an import of the cryptography namespace to the start of the file that contains the `Simple3Des` class.</span></span>  
  
     [!code-vb[VbVbalrStrings#77](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_2.vb)]  
  
3.  <span data-ttu-id="63097-115">V `Simple3Des` třídy, přidejte soukromé pole k uložení zprostředkovatele kryptografických služeb 3DES.</span><span class="sxs-lookup"><span data-stu-id="63097-115">In the `Simple3Des` class, add a private field to store the 3DES cryptographic service provider.</span></span>  
  
     [!code-vb[VbVbalrStrings#39](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_3.vb)]  
  
4.  <span data-ttu-id="63097-116">Přidejte soukromá metoda, která vytvoří bajtové pole o zadané délce z hodnota hash se zadaným klíčem.</span><span class="sxs-lookup"><span data-stu-id="63097-116">Add a private method that creates a byte array of a specified length from the hash of the specified key.</span></span>  
  
     [!code-vb[VbVbalrStrings#41](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_4.vb)]  
  
5.  <span data-ttu-id="63097-117">Přidejte konstruktor k inicializaci zprostředkovatele kryptografických služeb 3DES.</span><span class="sxs-lookup"><span data-stu-id="63097-117">Add a constructor to initialize the 3DES cryptographic service provider.</span></span>  
  
     <span data-ttu-id="63097-118">`key` Ovládací prvky parametrů `EncryptData` a `DecryptData` metody.</span><span class="sxs-lookup"><span data-stu-id="63097-118">The `key` parameter controls the `EncryptData` and `DecryptData` methods.</span></span>  
  
     [!code-vb[VbVbalrStrings#40](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_5.vb)]  
  
6.  <span data-ttu-id="63097-119">Přidejte veřejnou metodu, která zašifruje řetězec.</span><span class="sxs-lookup"><span data-stu-id="63097-119">Add a public method that encrypts a string.</span></span>  
  
     [!code-vb[VbVbalrStrings#42](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_6.vb)]  
  
7.  <span data-ttu-id="63097-120">Přidejte veřejnou metodu, která dešifruje řetězec.</span><span class="sxs-lookup"><span data-stu-id="63097-120">Add a public method that decrypts a string.</span></span>  
  
     [!code-vb[VbVbalrStrings#43](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_7.vb)]  
  
     <span data-ttu-id="63097-121">Obálková třída teď umožňuje chránit prostředky uživatele.</span><span class="sxs-lookup"><span data-stu-id="63097-121">The wrapper class can now be used to protect user assets.</span></span> <span data-ttu-id="63097-122">V tomto příkladu se používá bezpečně uložit privátních dat uživatele do veřejně přístupné textového souboru.</span><span class="sxs-lookup"><span data-stu-id="63097-122">In this example, it is used to securely store private user data in a publicly accessible text file.</span></span>  
  
### <a name="to-test-the-encryption-wrapper"></a><span data-ttu-id="63097-123">K testování obálku šifrování</span><span class="sxs-lookup"><span data-stu-id="63097-123">To test the encryption wrapper</span></span>  
  
1.  <span data-ttu-id="63097-124">V samostatné třídy, přidejte metodu, která používá obálku `EncryptData` metoda šifrování řetězec a zapsat pro uživatele je složka Dokumenty.</span><span class="sxs-lookup"><span data-stu-id="63097-124">In a separate class, add a method that uses the wrapper's `EncryptData` method to encrypt a string and write it to the user's My Documents folder.</span></span>  
  
     [!code-vb[VbVbalrStrings#78](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_8.vb)]  
  
2.  <span data-ttu-id="63097-125">Přidejte metodu, která čte zašifrovaný řetězec od uživatele je složka Dokumenty a dešifruje řetězec s Obálka `DecryptData` metoda.</span><span class="sxs-lookup"><span data-stu-id="63097-125">Add a method that reads the encrypted string from the user's My Documents folder and decrypts the string with the wrapper's `DecryptData` method.</span></span>  
  
     [!code-vb[VbVbalrStrings#79](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_9.vb)]  
  
3.  <span data-ttu-id="63097-126">Přidejte kód uživatelského rozhraní k volání `TestEncoding` a `TestDecoding` metody.</span><span class="sxs-lookup"><span data-stu-id="63097-126">Add user interface code to call the `TestEncoding` and `TestDecoding` methods.</span></span>  
  
4.  <span data-ttu-id="63097-127">Spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="63097-127">Run the application.</span></span>  
  
     <span data-ttu-id="63097-128">Při testování aplikace, Všimněte si data ho nebude dešifrovat, pokud jste zadali nesprávné heslo.</span><span class="sxs-lookup"><span data-stu-id="63097-128">When you test the application, notice that it will not decrypt the data if you provide the wrong password.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63097-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="63097-129">See Also</span></span>  
 <xref:System.Security.Cryptography>  
 <xref:System.Security.Cryptography.DESCryptoServiceProvider>  
 <xref:System.Security.Cryptography.DES>  
 <xref:System.Security.Cryptography.TripleDES>  
 <xref:System.Security.Cryptography.Rijndael>  
 [<span data-ttu-id="63097-130">Kryptografické služby</span><span class="sxs-lookup"><span data-stu-id="63097-130">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
