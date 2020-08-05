---
title: 'Návod: Vytvoření šifrovací aplikace'
description: Projděte si vytváření kryptografických aplikací. Naučte se šifrovat a dešifrovat obsah v model Windows Forms aplikaci.
ms.date: 07/14/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cryptography [NET], example
- cryptography [NET], cryptographic application example
- cryptography [NET], application example
ms.assetid: abf48c11-1e72-431d-9562-39cf23e1a8ff
ms.openlocfilehash: 16a887f23c584daa83106ae61c497bcae8dc4dd2
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/04/2020
ms.locfileid: "87557187"
---
# <a name="walkthrough-creating-a-cryptographic-application"></a><span data-ttu-id="cf08e-104">Návod: Vytvoření šifrovací aplikace</span><span class="sxs-lookup"><span data-stu-id="cf08e-104">Walkthrough: Creating a Cryptographic Application</span></span>

> [!NOTE]
> <span data-ttu-id="cf08e-105">Tento článek se týká systému Windows.</span><span class="sxs-lookup"><span data-stu-id="cf08e-105">This article applies to Windows.</span></span>
>
> <span data-ttu-id="cf08e-106">Informace o ASP.NET Core najdete v tématu [ASP.NET Core Data Protection](/aspnet/core/security/data-protection/introduction).</span><span class="sxs-lookup"><span data-stu-id="cf08e-106">For information about ASP.NET Core, see [ASP.NET Core Data Protection](/aspnet/core/security/data-protection/introduction).</span></span>

<span data-ttu-id="cf08e-107">Tento návod ukazuje, jak šifrovat a dešifrovat obsah.</span><span class="sxs-lookup"><span data-stu-id="cf08e-107">This walkthrough demonstrates how to encrypt and decrypt content.</span></span> <span data-ttu-id="cf08e-108">Příklady kódu jsou určeny pro model Windows Forms aplikace.</span><span class="sxs-lookup"><span data-stu-id="cf08e-108">The code examples are designed for a Windows Forms application.</span></span> <span data-ttu-id="cf08e-109">Tato aplikace nemonstruje scénáře reálného světa, jako je například použití čipových karet.</span><span class="sxs-lookup"><span data-stu-id="cf08e-109">This application does not demonstrate real world scenarios, such as using smart cards.</span></span> <span data-ttu-id="cf08e-110">Místo toho ukazuje základy šifrování a dešifrování.</span><span class="sxs-lookup"><span data-stu-id="cf08e-110">Instead, it demonstrates the fundamentals of encryption and decryption.</span></span>  
  
<span data-ttu-id="cf08e-111">Tento návod používá pro šifrování následující pokyny:</span><span class="sxs-lookup"><span data-stu-id="cf08e-111">This walkthrough uses the following guidelines for encryption:</span></span>  
  
- <span data-ttu-id="cf08e-112">Použijte <xref:System.Security.Cryptography.Aes> třídu, symetrický algoritmus pro šifrování a dešifrování dat pomocí automatického vygenerovaného <xref:System.Security.Cryptography.SymmetricAlgorithm.Key%2A> a <xref:System.Security.Cryptography.SymmetricAlgorithm.IV%2A> .</span><span class="sxs-lookup"><span data-stu-id="cf08e-112">Use the <xref:System.Security.Cryptography.Aes> class, a symmetric algorithm, to encrypt and decrypt data by using its automatically generated <xref:System.Security.Cryptography.SymmetricAlgorithm.Key%2A> and <xref:System.Security.Cryptography.SymmetricAlgorithm.IV%2A>.</span></span>  
  
- <span data-ttu-id="cf08e-113">Pomocí <xref:System.Security.Cryptography.RSA> asymetrického algoritmu Zašifrujte a dešifrujte klíč na data zašifrovaná nástrojem <xref:System.Security.Cryptography.Aes> .</span><span class="sxs-lookup"><span data-stu-id="cf08e-113">Use the <xref:System.Security.Cryptography.RSA> asymmetric algorithm to encrypt and decrypt the key to the data encrypted by <xref:System.Security.Cryptography.Aes>.</span></span> <span data-ttu-id="cf08e-114">Asymetrické algoritmy se nejlépe používají pro menší objemy dat, jako je například klíč.</span><span class="sxs-lookup"><span data-stu-id="cf08e-114">Asymmetric algorithms are best used for smaller amounts of data, such as a key.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="cf08e-115">Chcete-li chránit data v počítači namísto výměny šifrovaného obsahu s jinými lidmi, zvažte použití <xref:System.Security.Cryptography.ProtectedData> třídy.</span><span class="sxs-lookup"><span data-stu-id="cf08e-115">If you want to protect data on your computer instead of exchanging encrypted content with other people, consider using the <xref:System.Security.Cryptography.ProtectedData> class.</span></span>  
  
 <span data-ttu-id="cf08e-116">Následující tabulka shrnuje kryptografické úlohy v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="cf08e-116">The following table summarizes the cryptographic tasks in this topic.</span></span>  
  
|<span data-ttu-id="cf08e-117">Úkol</span><span class="sxs-lookup"><span data-stu-id="cf08e-117">Task</span></span>|<span data-ttu-id="cf08e-118">Popis</span><span class="sxs-lookup"><span data-stu-id="cf08e-118">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="cf08e-119">Vytvoření aplikace model Windows Forms</span><span class="sxs-lookup"><span data-stu-id="cf08e-119">Creating a Windows Forms application</span></span>|<span data-ttu-id="cf08e-120">Seznam ovládacích prvků, které jsou požadovány ke spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="cf08e-120">Lists the controls that are required to run the application.</span></span>|  
|<span data-ttu-id="cf08e-121">Deklarace globálních objektů</span><span class="sxs-lookup"><span data-stu-id="cf08e-121">Declaring global objects</span></span>|<span data-ttu-id="cf08e-122">Deklaruje proměnné cesty k řetězci, <xref:System.Security.Cryptography.CspParameters> a a má <xref:System.Security.Cryptography.RSACryptoServiceProvider> globální kontext <xref:System.Windows.Forms.Form> třídy.</span><span class="sxs-lookup"><span data-stu-id="cf08e-122">Declares string path variables, the <xref:System.Security.Cryptography.CspParameters>, and the <xref:System.Security.Cryptography.RSACryptoServiceProvider> to have global context of the <xref:System.Windows.Forms.Form> class.</span></span>|  
|<span data-ttu-id="cf08e-123">Vytváření asymetrického klíče</span><span class="sxs-lookup"><span data-stu-id="cf08e-123">Creating an asymmetric key</span></span>|<span data-ttu-id="cf08e-124">Vytvoří asymetrickou dvojici hodnot veřejného a privátního klíče a přiřadí jí název kontejneru klíčů.</span><span class="sxs-lookup"><span data-stu-id="cf08e-124">Creates an asymmetric public and private key value pair and assigns it a key container name.</span></span>|  
|<span data-ttu-id="cf08e-125">Šifrování souboru</span><span class="sxs-lookup"><span data-stu-id="cf08e-125">Encrypting a file</span></span>|<span data-ttu-id="cf08e-126">Zobrazí dialogové okno pro výběr souboru pro šifrování a zašifruje soubor.</span><span class="sxs-lookup"><span data-stu-id="cf08e-126">Displays a dialog box to select a file for encryption and encrypts the file.</span></span>|  
|<span data-ttu-id="cf08e-127">Dešifrování souboru</span><span class="sxs-lookup"><span data-stu-id="cf08e-127">Decrypting a file</span></span>|<span data-ttu-id="cf08e-128">Zobrazí dialogové okno, ve kterém můžete vybrat zašifrovaný soubor pro dešifrování a dešifrovat soubor.</span><span class="sxs-lookup"><span data-stu-id="cf08e-128">Displays a dialog box to select an encrypted file for decryption and decrypts the file.</span></span>|  
|<span data-ttu-id="cf08e-129">Získání privátního klíče</span><span class="sxs-lookup"><span data-stu-id="cf08e-129">Getting a private key</span></span>|<span data-ttu-id="cf08e-130">Získá úplnou dvojici klíčů pomocí názvu kontejneru klíčů.</span><span class="sxs-lookup"><span data-stu-id="cf08e-130">Gets the full key pair using the key container name.</span></span>|  
|<span data-ttu-id="cf08e-131">Export veřejného klíče</span><span class="sxs-lookup"><span data-stu-id="cf08e-131">Exporting a public key</span></span>|<span data-ttu-id="cf08e-132">Uloží klíč do souboru XML s pouze veřejnými parametry.</span><span class="sxs-lookup"><span data-stu-id="cf08e-132">Saves the key to an XML file with only public parameters.</span></span>|  
|<span data-ttu-id="cf08e-133">Import veřejného klíče</span><span class="sxs-lookup"><span data-stu-id="cf08e-133">Importing a public key</span></span>|<span data-ttu-id="cf08e-134">Načte klíč ze souboru XML do kontejneru klíčů.</span><span class="sxs-lookup"><span data-stu-id="cf08e-134">Loads the key from an XML file into the key container.</span></span>|  
|<span data-ttu-id="cf08e-135">Testování aplikace</span><span class="sxs-lookup"><span data-stu-id="cf08e-135">Testing the application</span></span>|<span data-ttu-id="cf08e-136">Uvádí postupy pro testování této aplikace.</span><span class="sxs-lookup"><span data-stu-id="cf08e-136">Lists procedures for testing this application.</span></span>|  
  
## <a name="prerequisites"></a><span data-ttu-id="cf08e-137">Předpoklady</span><span class="sxs-lookup"><span data-stu-id="cf08e-137">Prerequisites</span></span>  

<span data-ttu-id="cf08e-138">K dokončení tohoto návodu budete potřebovat následující komponenty:</span><span class="sxs-lookup"><span data-stu-id="cf08e-138">You need the following components to complete this walkthrough:</span></span>  
  
- <span data-ttu-id="cf08e-139">Odkazy na <xref:System.IO> <xref:System.Security.Cryptography> obory názvů a.</span><span class="sxs-lookup"><span data-stu-id="cf08e-139">References to the <xref:System.IO> and <xref:System.Security.Cryptography> namespaces.</span></span>  
  
## <a name="creating-a-windows-forms-application"></a><span data-ttu-id="cf08e-140">Vytvoření aplikace model Windows Forms</span><span class="sxs-lookup"><span data-stu-id="cf08e-140">Creating a Windows Forms Application</span></span>  

<span data-ttu-id="cf08e-141">Většina příkladů kódu v tomto návodu je navržena jako obslužné rutiny událostí pro ovládací prvky tlačítek.</span><span class="sxs-lookup"><span data-stu-id="cf08e-141">Most of the code examples in this walkthrough are designed to be event handlers for button controls.</span></span> <span data-ttu-id="cf08e-142">V následující tabulce jsou uvedeny ovládací prvky požadované pro ukázkovou aplikaci a jejich požadované názvy, aby odpovídaly příkladům kódu.</span><span class="sxs-lookup"><span data-stu-id="cf08e-142">The following table lists the controls required for the sample application and their required names to match the code examples.</span></span>  
  
|<span data-ttu-id="cf08e-143">Řízení</span><span class="sxs-lookup"><span data-stu-id="cf08e-143">Control</span></span>|<span data-ttu-id="cf08e-144">Název</span><span class="sxs-lookup"><span data-stu-id="cf08e-144">Name</span></span>|<span data-ttu-id="cf08e-145">Vlastnost text (podle potřeby)</span><span class="sxs-lookup"><span data-stu-id="cf08e-145">Text property (as needed)</span></span>|  
|-------------|----------|---------------------------------|  
|<xref:System.Windows.Forms.Button>|`buttonEncryptFile`|<span data-ttu-id="cf08e-146">Šifrovat soubor</span><span class="sxs-lookup"><span data-stu-id="cf08e-146">Encrypt File</span></span>|  
|<xref:System.Windows.Forms.Button>|`buttonDecryptFile`|<span data-ttu-id="cf08e-147">Dešifrovat soubor</span><span class="sxs-lookup"><span data-stu-id="cf08e-147">Decrypt File</span></span>|  
|<xref:System.Windows.Forms.Button>|`buttonCreateAsmKeys`|<span data-ttu-id="cf08e-148">Vytvořit klíče</span><span class="sxs-lookup"><span data-stu-id="cf08e-148">Create Keys</span></span>|  
|<xref:System.Windows.Forms.Button>|`buttonExportPublicKey`|<span data-ttu-id="cf08e-149">Exportovat veřejný klíč</span><span class="sxs-lookup"><span data-stu-id="cf08e-149">Export Public Key</span></span>|  
|<xref:System.Windows.Forms.Button>|`buttonImportPublicKey`|<span data-ttu-id="cf08e-150">Importovat veřejný klíč</span><span class="sxs-lookup"><span data-stu-id="cf08e-150">Import Public Key</span></span>|  
|<xref:System.Windows.Forms.Button>|`buttonGetPrivateKey`|<span data-ttu-id="cf08e-151">Získat privátní klíč</span><span class="sxs-lookup"><span data-stu-id="cf08e-151">Get Private Key</span></span>|  
|<xref:System.Windows.Forms.Label>|`label1`|<span data-ttu-id="cf08e-152">Klíč není nastaven.</span><span class="sxs-lookup"><span data-stu-id="cf08e-152">Key not set</span></span>|  
|<xref:System.Windows.Forms.OpenFileDialog>|`openFileDialog1`||  
|<xref:System.Windows.Forms.OpenFileDialog>|`openFileDialog2`||  
  
 <span data-ttu-id="cf08e-153">Dvojím kliknutím na tlačítka v návrháři sady Visual Studio vytvořte obslužné rutiny událostí.</span><span class="sxs-lookup"><span data-stu-id="cf08e-153">Double-click the buttons in the Visual Studio designer to create their event handlers.</span></span>
  
## <a name="declaring-global-objects"></a><span data-ttu-id="cf08e-154">Deklarace globálních objektů</span><span class="sxs-lookup"><span data-stu-id="cf08e-154">Declaring Global Objects</span></span>  

<span data-ttu-id="cf08e-155">Do konstruktoru formuláře přidejte následující kód.</span><span class="sxs-lookup"><span data-stu-id="cf08e-155">Add the following code to the Form's constructor.</span></span> <span data-ttu-id="cf08e-156">Upravte řetězcové proměnné pro vaše prostředí a předvolby.</span><span class="sxs-lookup"><span data-stu-id="cf08e-156">Edit the string variables for your environment and preferences.</span></span>  
  
[!code-csharp[CryptoWalkThru#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#1)]
[!code-vb[CryptoWalkThru#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#1)]  
  
## <a name="creating-an-asymmetric-key"></a><span data-ttu-id="cf08e-157">Vytváření asymetrického klíče</span><span class="sxs-lookup"><span data-stu-id="cf08e-157">Creating an Asymmetric Key</span></span>  

<span data-ttu-id="cf08e-158">Tato úloha vytvoří asymetrický klíč, který šifruje a dešifruje <xref:System.Security.Cryptography.Aes> klíč.</span><span class="sxs-lookup"><span data-stu-id="cf08e-158">This task creates an asymmetric key that encrypts and decrypts the <xref:System.Security.Cryptography.Aes> key.</span></span> <span data-ttu-id="cf08e-159">Tento klíč se použil k zašifrování obsahu a zobrazuje název kontejneru klíčů v ovládacím prvku popisek.</span><span class="sxs-lookup"><span data-stu-id="cf08e-159">This key was used to encrypt the content and it displays the key container name on the label control.</span></span>  
  
 <span data-ttu-id="cf08e-160">Přidejte následující kód jako `Click` obslužnou rutinu události pro `Create Keys` tlačítko ( `buttonCreateAsmKeys_Click` ).</span><span class="sxs-lookup"><span data-stu-id="cf08e-160">Add the following code as the `Click` event handler for the `Create Keys` button (`buttonCreateAsmKeys_Click`).</span></span>  
  
 [!code-csharp[CryptoWalkThru#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#2)]
 [!code-vb[CryptoWalkThru#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#2)]  
  
## <a name="encrypting-a-file"></a><span data-ttu-id="cf08e-161">Šifrování souboru</span><span class="sxs-lookup"><span data-stu-id="cf08e-161">Encrypting a File</span></span>  

<span data-ttu-id="cf08e-162">Tato úloha zahrnuje dvě metody: metodu obslužné rutiny události pro `Encrypt File` tlačítko ( `buttonEncryptFile_Click` ) a `EncryptFile` metodu.</span><span class="sxs-lookup"><span data-stu-id="cf08e-162">This task involves two methods: the event handler method for the `Encrypt File` button (`buttonEncryptFile_Click`) and the `EncryptFile` method.</span></span> <span data-ttu-id="cf08e-163">První metoda zobrazí dialogové okno pro výběr souboru a předá název souboru druhé metodě, která provádí šifrování.</span><span class="sxs-lookup"><span data-stu-id="cf08e-163">The first method displays a dialog box for selecting a file and passes the file name to the second method, which performs the encryption.</span></span>  
  
<span data-ttu-id="cf08e-164">Zašifrovaný obsah, klíč a IV jsou uloženy do jednoho <xref:System.IO.FileStream> , který je označován jako balíček šifrování.</span><span class="sxs-lookup"><span data-stu-id="cf08e-164">The encrypted content, key, and IV are all saved to one <xref:System.IO.FileStream>, which is referred to as the encryption package.</span></span>  
  
<span data-ttu-id="cf08e-165">`EncryptFile`Metoda provede následující akce:</span><span class="sxs-lookup"><span data-stu-id="cf08e-165">The `EncryptFile` method does the following:</span></span>  
  
1. <span data-ttu-id="cf08e-166">Vytvoří <xref:System.Security.Cryptography.Aes> symetrický algoritmus pro šifrování obsahu.</span><span class="sxs-lookup"><span data-stu-id="cf08e-166">Creates a <xref:System.Security.Cryptography.Aes> symmetric algorithm to encrypt the content.</span></span>  
  
2. <span data-ttu-id="cf08e-167">Vytvoří <xref:System.Security.Cryptography.RSACryptoServiceProvider> objekt pro šifrování <xref:System.Security.Cryptography.Aes> klíče.</span><span class="sxs-lookup"><span data-stu-id="cf08e-167">Creates an <xref:System.Security.Cryptography.RSACryptoServiceProvider> object to encrypt the <xref:System.Security.Cryptography.Aes> key.</span></span>  
  
3. <span data-ttu-id="cf08e-168">Používá <xref:System.Security.Cryptography.CryptoStream> objekt ke čtení a šifrování <xref:System.IO.FileStream> zdrojového souboru, v blocích bajtů, do cílového <xref:System.IO.FileStream> objektu pro zašifrovaný soubor.</span><span class="sxs-lookup"><span data-stu-id="cf08e-168">Uses a <xref:System.Security.Cryptography.CryptoStream> object to read and encrypt the <xref:System.IO.FileStream> of the source file, in blocks of bytes, into a destination <xref:System.IO.FileStream> object for the encrypted file.</span></span>  
  
4. <span data-ttu-id="cf08e-169">Určuje délku šifrovaného klíče a IV a vytvoří pole bajtů jejich hodnot délky.</span><span class="sxs-lookup"><span data-stu-id="cf08e-169">Determines the lengths of the encrypted key and IV, and creates byte arrays of their length values.</span></span>  
  
5. <span data-ttu-id="cf08e-170">Zapíše klíč, IV a jejich hodnoty délky do šifrovaného balíčku.</span><span class="sxs-lookup"><span data-stu-id="cf08e-170">Writes the Key, IV, and their length values to the encrypted package.</span></span>  
  
 <span data-ttu-id="cf08e-171">Šifrovací balíček používá následující formát:</span><span class="sxs-lookup"><span data-stu-id="cf08e-171">The encryption package uses the following format:</span></span>  
  
- <span data-ttu-id="cf08e-172">Délka klíče, bajty 0-3</span><span class="sxs-lookup"><span data-stu-id="cf08e-172">Key length, bytes 0 - 3</span></span>  
  
- <span data-ttu-id="cf08e-173">Délka IV, bajty 4-7</span><span class="sxs-lookup"><span data-stu-id="cf08e-173">IV length, bytes 4 - 7</span></span>  
  
- <span data-ttu-id="cf08e-174">Šifrovaný klíč</span><span class="sxs-lookup"><span data-stu-id="cf08e-174">Encrypted key</span></span>  
  
- <span data-ttu-id="cf08e-175">IV</span><span class="sxs-lookup"><span data-stu-id="cf08e-175">IV</span></span>  
  
- <span data-ttu-id="cf08e-176">Šifrovaný text</span><span class="sxs-lookup"><span data-stu-id="cf08e-176">Cipher text</span></span>  
  
 <span data-ttu-id="cf08e-177">Délku klíče a IV můžete použít k určení počátečních bodů a délek všech částí šifrovacího balíčku, které pak můžete použít k dešifrování souboru.</span><span class="sxs-lookup"><span data-stu-id="cf08e-177">You can use the lengths of the key and IV to determine the starting points and lengths of all parts of the encryption package, which can then be used to decrypt the file.</span></span>  
  
 <span data-ttu-id="cf08e-178">Přidejte následující kód jako `Click` obslužnou rutinu události pro `Encrypt File` tlačítko ( `buttonEncryptFile_Click` ).</span><span class="sxs-lookup"><span data-stu-id="cf08e-178">Add the following code as the `Click` event handler for the `Encrypt File` button (`buttonEncryptFile_Click`).</span></span>  
  
 [!code-csharp[CryptoWalkThru#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#3)]
 [!code-vb[CryptoWalkThru#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#3)]  
  
 <span data-ttu-id="cf08e-179">`EncryptFile`Do formuláře přidejte následující metodu.</span><span class="sxs-lookup"><span data-stu-id="cf08e-179">Add the following `EncryptFile` method to the form.</span></span>  
  
 [!code-csharp[CryptoWalkThru#5](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#5)]
 [!code-vb[CryptoWalkThru#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#5)]  
  
## <a name="decrypting-a-file"></a><span data-ttu-id="cf08e-180">Dešifrování souboru</span><span class="sxs-lookup"><span data-stu-id="cf08e-180">Decrypting a File</span></span>  

<span data-ttu-id="cf08e-181">Tato úloha zahrnuje dvě metody, metodu obslužné rutiny události pro `Decrypt File` tlačítko ( `buttonDecryptFile_Click` ) a `DecryptFile` metodu.</span><span class="sxs-lookup"><span data-stu-id="cf08e-181">This task involves two methods, the event handler method for the `Decrypt File` button (`buttonDecryptFile_Click`), and the `DecryptFile` method.</span></span> <span data-ttu-id="cf08e-182">První metoda zobrazí dialogové okno pro výběr souboru a předá jeho název souboru druhé metodě, která provádí dešifrování.</span><span class="sxs-lookup"><span data-stu-id="cf08e-182">The first method displays a dialog box for selecting a file and passes its file name to the second method, which performs the decryption.</span></span>  
  
<span data-ttu-id="cf08e-183">`Decrypt`Metoda provede následující akce:</span><span class="sxs-lookup"><span data-stu-id="cf08e-183">The `Decrypt` method does the following:</span></span>  
  
1. <span data-ttu-id="cf08e-184">Vytvoří <xref:System.Security.Cryptography.Aes> symetrický algoritmus pro dešifrování obsahu.</span><span class="sxs-lookup"><span data-stu-id="cf08e-184">Creates an <xref:System.Security.Cryptography.Aes> symmetric algorithm to decrypt the content.</span></span>  
  
2. <span data-ttu-id="cf08e-185">Přečte prvních osm bajtů <xref:System.IO.FileStream> zašifrovaného balíčku do polí bajtů, aby získala délky šifrovaného klíče a IV.</span><span class="sxs-lookup"><span data-stu-id="cf08e-185">Reads the first eight bytes of the <xref:System.IO.FileStream> of the encrypted package into byte arrays to obtain the lengths of the encrypted key and the IV.</span></span>  
  
3. <span data-ttu-id="cf08e-186">Extrahuje klíč a IV z šifrovacího balíčku do polí bajtů.</span><span class="sxs-lookup"><span data-stu-id="cf08e-186">Extracts the key and IV from the encryption package into byte arrays.</span></span>  
  
4. <span data-ttu-id="cf08e-187">Vytvoří <xref:System.Security.Cryptography.RSACryptoServiceProvider> objekt pro dešifrování <xref:System.Security.Cryptography.Aes> klíče.</span><span class="sxs-lookup"><span data-stu-id="cf08e-187">Creates an <xref:System.Security.Cryptography.RSACryptoServiceProvider> object to decrypt the <xref:System.Security.Cryptography.Aes> key.</span></span>  
  
5. <span data-ttu-id="cf08e-188">Používá <xref:System.Security.Cryptography.CryptoStream> objekt pro čtení a dešifrování oddílu šifry textu <xref:System.IO.FileStream> v balíčku šifrování v blocích bajtů do <xref:System.IO.FileStream> objektu pro dešifrovaný soubor.</span><span class="sxs-lookup"><span data-stu-id="cf08e-188">Uses a <xref:System.Security.Cryptography.CryptoStream> object to read and decrypt the cipher text section of the <xref:System.IO.FileStream> encryption package, in blocks of bytes, into the <xref:System.IO.FileStream> object for the decrypted file.</span></span> <span data-ttu-id="cf08e-189">Po dokončení se dešifrování dokončí.</span><span class="sxs-lookup"><span data-stu-id="cf08e-189">When this is finished, the decryption is completed.</span></span>  
  
 <span data-ttu-id="cf08e-190">Přidejte následující kód jako `Click` obslužnou rutinu události pro `Decrypt File` tlačítko.</span><span class="sxs-lookup"><span data-stu-id="cf08e-190">Add the following code as the `Click` event handler for the `Decrypt File` button.</span></span>  
  
 [!code-csharp[CryptoWalkThru#4](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#4)]
 [!code-vb[CryptoWalkThru#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#4)]  
  
 <span data-ttu-id="cf08e-191">`DecryptFile`Do formuláře přidejte následující metodu.</span><span class="sxs-lookup"><span data-stu-id="cf08e-191">Add the following `DecryptFile` method to the form.</span></span>  
  
 [!code-csharp[CryptoWalkThru#6](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#6)]
 [!code-vb[CryptoWalkThru#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#6)]  
  
## <a name="exporting-a-public-key"></a><span data-ttu-id="cf08e-192">Export veřejného klíče</span><span class="sxs-lookup"><span data-stu-id="cf08e-192">Exporting a Public Key</span></span>

<span data-ttu-id="cf08e-193">Tento úkol uloží klíč vytvořený `Create Keys` tlačítkem do souboru.</span><span class="sxs-lookup"><span data-stu-id="cf08e-193">This task saves the key created by the `Create Keys` button to a file.</span></span> <span data-ttu-id="cf08e-194">Exportuje pouze veřejné parametry.</span><span class="sxs-lookup"><span data-stu-id="cf08e-194">It exports only the public parameters.</span></span>  
  
<span data-ttu-id="cf08e-195">Tato úloha simuluje scénář Alice, která dává Bobovi veřejný klíč, aby k nim mohl šifrovat soubory.</span><span class="sxs-lookup"><span data-stu-id="cf08e-195">This task simulates the scenario of Alice giving Bob her public key so that he can encrypt files for her.</span></span> <span data-ttu-id="cf08e-196">A ostatní, kteří mají tento veřejný klíč, nebudou schopni je dešifrovat, protože nemají úplný pár klíčů s privátními parametry.</span><span class="sxs-lookup"><span data-stu-id="cf08e-196">He and others who have that public key will not be able to decrypt them because they do not have the full key pair with private parameters.</span></span>  
  
<span data-ttu-id="cf08e-197">Přidejte následující kód jako `Click` obslužnou rutinu události pro `Export Public Key` tlačítko ( `buttonExportPublicKey_Click` ).</span><span class="sxs-lookup"><span data-stu-id="cf08e-197">Add the following code as the `Click` event handler for the `Export Public Key` button (`buttonExportPublicKey_Click`).</span></span>  
  
[!code-csharp[CryptoWalkThru#8](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#8)]
[!code-vb[CryptoWalkThru#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#8)]  
  
## <a name="importing-a-public-key"></a><span data-ttu-id="cf08e-198">Import veřejného klíče</span><span class="sxs-lookup"><span data-stu-id="cf08e-198">Importing a Public Key</span></span>

<span data-ttu-id="cf08e-199">Tato úloha načte klíč jenom s veřejnými parametry, jak je vytvořil `Export Public Key` tlačítko, a nastaví ho jako název kontejneru klíčů.</span><span class="sxs-lookup"><span data-stu-id="cf08e-199">This task loads the key with only public parameters, as created by the `Export Public Key` button, and sets it as the key container name.</span></span>  
  
<span data-ttu-id="cf08e-200">Tato úloha simuluje scénář, který Bob načítá klíč Alice, jenom s veřejnými parametry, aby k nim mohl šifrovat soubory.</span><span class="sxs-lookup"><span data-stu-id="cf08e-200">This task simulates the scenario of Bob loading Alice's key with only public parameters so he can encrypt files for her.</span></span>  
  
<span data-ttu-id="cf08e-201">Přidejte následující kód jako `Click` obslužnou rutinu události pro `Import Public Key` tlačítko ( `buttonImportPublicKey_Click` ).</span><span class="sxs-lookup"><span data-stu-id="cf08e-201">Add the following code as the `Click` event handler for the `Import Public Key` button (`buttonImportPublicKey_Click`).</span></span>  
  
[!code-csharp[CryptoWalkThru#9](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#9)]
[!code-vb[CryptoWalkThru#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#9)]  
  
## <a name="getting-a-private-key"></a><span data-ttu-id="cf08e-202">Získání privátního klíče</span><span class="sxs-lookup"><span data-stu-id="cf08e-202">Getting a Private Key</span></span>  

<span data-ttu-id="cf08e-203">Tato úloha nastaví název kontejneru klíčů na název klíče vytvořeného pomocí `Create Keys` tlačítka.</span><span class="sxs-lookup"><span data-stu-id="cf08e-203">This task sets the key container name to the name of the key created by using the `Create Keys` button.</span></span> <span data-ttu-id="cf08e-204">Kontejner klíčů bude obsahovat úplný pár klíčů s privátními parametry.</span><span class="sxs-lookup"><span data-stu-id="cf08e-204">The key container will contain the full key pair with private parameters.</span></span>  
  
<span data-ttu-id="cf08e-205">Tato úloha simuluje scénář Alice, který používá svůj privátní klíč k dešifrování souborů šifrovaných Bobem.</span><span class="sxs-lookup"><span data-stu-id="cf08e-205">This task simulates the scenario of Alice using her private key to decrypt files encrypted by Bob.</span></span>  
  
<span data-ttu-id="cf08e-206">Přidejte následující kód jako `Click` obslužnou rutinu události pro `Get Private Key` tlačítko ( `buttonGetPrivateKey_Click` ).</span><span class="sxs-lookup"><span data-stu-id="cf08e-206">Add the following code as the `Click` event handler for the `Get Private Key` button (`buttonGetPrivateKey_Click`).</span></span>  
  
[!code-csharp[CryptoWalkThru#7](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#7)]
[!code-vb[CryptoWalkThru#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#7)]  
  
## <a name="testing-the-application"></a><span data-ttu-id="cf08e-207">Testování aplikace</span><span class="sxs-lookup"><span data-stu-id="cf08e-207">Testing the Application</span></span>

<span data-ttu-id="cf08e-208">Po vytvoření aplikace proveďte následující testovací scénáře.</span><span class="sxs-lookup"><span data-stu-id="cf08e-208">After you have built the application, perform the following testing scenarios.</span></span>  
  
#### <a name="to-create-keys-encrypt-and-decrypt"></a><span data-ttu-id="cf08e-209">Vytvoření klíčů, šifrování a dešifrování</span><span class="sxs-lookup"><span data-stu-id="cf08e-209">To create keys, encrypt, and decrypt</span></span>  
  
1. <span data-ttu-id="cf08e-210">Klikněte na tlačítko `Create Keys`.</span><span class="sxs-lookup"><span data-stu-id="cf08e-210">Click the `Create Keys` button.</span></span> <span data-ttu-id="cf08e-211">Popisek zobrazí název klíče a ukáže, že se jedná o úplný pár klíčů.</span><span class="sxs-lookup"><span data-stu-id="cf08e-211">The label displays the key name and shows that it is a full key pair.</span></span>  
  
2. <span data-ttu-id="cf08e-212">Klikněte na tlačítko `Export Public Key`.</span><span class="sxs-lookup"><span data-stu-id="cf08e-212">Click the `Export Public Key` button.</span></span> <span data-ttu-id="cf08e-213">Všimněte si, že export parametrů veřejného klíče nemění aktuální klíč.</span><span class="sxs-lookup"><span data-stu-id="cf08e-213">Note that exporting the public key parameters does not change the current key.</span></span>  
  
3. <span data-ttu-id="cf08e-214">Klikněte na `Encrypt File` tlačítko a vyberte soubor.</span><span class="sxs-lookup"><span data-stu-id="cf08e-214">Click the `Encrypt File` button and select a file.</span></span>  
  
4. <span data-ttu-id="cf08e-215">Klikněte na `Decrypt File` tlačítko a vyberte soubor právě zašifrovaný.</span><span class="sxs-lookup"><span data-stu-id="cf08e-215">Click the `Decrypt File` button and select the file just encrypted.</span></span>  
  
5. <span data-ttu-id="cf08e-216">Prověřte soubor, který se právě dešifroval.</span><span class="sxs-lookup"><span data-stu-id="cf08e-216">Examine the file just decrypted.</span></span>  
  
6. <span data-ttu-id="cf08e-217">Zavřete aplikaci a restartujte ji, abyste v dalším scénáři otestovali načtení trvalých kontejnerů klíčů.</span><span class="sxs-lookup"><span data-stu-id="cf08e-217">Close the application and restart it to test retrieving persisted key containers in the next scenario.</span></span>  
  
#### <a name="to-encrypt-using-the-public-key"></a><span data-ttu-id="cf08e-218">Šifrování pomocí veřejného klíče</span><span class="sxs-lookup"><span data-stu-id="cf08e-218">To encrypt using the public key</span></span>  
  
1. <span data-ttu-id="cf08e-219">Klikněte na tlačítko `Import Public Key`.</span><span class="sxs-lookup"><span data-stu-id="cf08e-219">Click the `Import Public Key` button.</span></span> <span data-ttu-id="cf08e-220">Popisek zobrazí název klíče a ukáže, že je pouze veřejný.</span><span class="sxs-lookup"><span data-stu-id="cf08e-220">The label displays the key name and shows that it is public only.</span></span>  
  
2. <span data-ttu-id="cf08e-221">Klikněte na `Encrypt File` tlačítko a vyberte soubor.</span><span class="sxs-lookup"><span data-stu-id="cf08e-221">Click the `Encrypt File` button and select a file.</span></span>  
  
3. <span data-ttu-id="cf08e-222">Klikněte na `Decrypt File` tlačítko a vyberte soubor právě zašifrovaný.</span><span class="sxs-lookup"><span data-stu-id="cf08e-222">Click the `Decrypt File` button and select the file just encrypted.</span></span> <span data-ttu-id="cf08e-223">To se nezdaří, protože musíte mít privátní klíč k dešifrování.</span><span class="sxs-lookup"><span data-stu-id="cf08e-223">This will fail because you must have the private key to decrypt.</span></span>  
  
 <span data-ttu-id="cf08e-224">Tento scénář ukazuje pouze veřejný klíč k šifrování souboru pro jinou osobu.</span><span class="sxs-lookup"><span data-stu-id="cf08e-224">This scenario demonstrates having only the public key to encrypt a file for another person.</span></span> <span data-ttu-id="cf08e-225">Obvykle vám někdo poskytne jenom veřejný klíč a odpírá privátní klíč k dešifrování.</span><span class="sxs-lookup"><span data-stu-id="cf08e-225">Typically that person would give you only the public key and withhold the private key for decryption.</span></span>  
  
#### <a name="to-decrypt-using-the-private-key"></a><span data-ttu-id="cf08e-226">Dešifrování pomocí privátního klíče</span><span class="sxs-lookup"><span data-stu-id="cf08e-226">To decrypt using the private key</span></span>  
  
1. <span data-ttu-id="cf08e-227">Klikněte na tlačítko `Get Private Key`.</span><span class="sxs-lookup"><span data-stu-id="cf08e-227">Click the `Get Private Key` button.</span></span> <span data-ttu-id="cf08e-228">Popisek zobrazí název klíče a ukáže, zda se jedná o úplný pár klíčů.</span><span class="sxs-lookup"><span data-stu-id="cf08e-228">The label displays the key name and shows whether it is the full key pair.</span></span>  
  
2. <span data-ttu-id="cf08e-229">Klikněte na `Decrypt File` tlačítko a vyberte soubor právě zašifrovaný.</span><span class="sxs-lookup"><span data-stu-id="cf08e-229">Click the `Decrypt File` button and select the file just encrypted.</span></span> <span data-ttu-id="cf08e-230">Tato akce bude úspěšná, protože máte úplný pár klíčů k dešifrování.</span><span class="sxs-lookup"><span data-stu-id="cf08e-230">This will be successful because you have the full key pair to decrypt.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf08e-231">Viz také</span><span class="sxs-lookup"><span data-stu-id="cf08e-231">See also</span></span>

- <span data-ttu-id="cf08e-232">[Kryptografický model](cryptography-model.md) – popisuje, jak je kryptografie implementována v knihovně základní třídy.</span><span class="sxs-lookup"><span data-stu-id="cf08e-232">[Cryptography Model](cryptography-model.md) - Describes how cryptography is implemented in the base class library.</span></span>
- [<span data-ttu-id="cf08e-233">Šifrovací služby</span><span class="sxs-lookup"><span data-stu-id="cf08e-233">Cryptographic Services</span></span>](cryptographic-services.md)
- [<span data-ttu-id="cf08e-234">Kryptografie pro různé platformy</span><span class="sxs-lookup"><span data-stu-id="cf08e-234">Cross-Platform Cryptography</span></span>](cross-platform-cryptography.md)
- [<span data-ttu-id="cf08e-235">Ochrana dat ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="cf08e-235">ASP.NET Core Data Protection</span></span>](/aspnet/core/security/data-protection/introduction)
