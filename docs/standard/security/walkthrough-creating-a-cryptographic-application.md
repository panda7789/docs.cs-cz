---
title: 'Návod: Vytvoření šifrovací aplikace'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cryptography [NET Framework], example
- cryptography [NET Framework], cryptographic application example
- cryptography [NET Framework], application example
ms.assetid: abf48c11-1e72-431d-9562-39cf23e1a8ff
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ee6dafa8578c59d23908bf0e184091bb4ceaeb45
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2019
ms.locfileid: "70895283"
---
# <a name="walkthrough-creating-a-cryptographic-application"></a><span data-ttu-id="de2a2-102">Návod: Vytvoření šifrovací aplikace</span><span class="sxs-lookup"><span data-stu-id="de2a2-102">Walkthrough: Creating a Cryptographic Application</span></span>
<span data-ttu-id="de2a2-103">Tento návod ukazuje, jak šifrovat a dešifrovat obsah.</span><span class="sxs-lookup"><span data-stu-id="de2a2-103">This walkthrough demonstrates how to encrypt and decrypt content.</span></span> <span data-ttu-id="de2a2-104">Příklady kódu jsou určeny pro model Windows Forms aplikace.</span><span class="sxs-lookup"><span data-stu-id="de2a2-104">The code examples are designed for a Windows Forms application.</span></span> <span data-ttu-id="de2a2-105">Tato aplikace nemonstruje scénáře reálného světa, jako je například použití čipových karet.</span><span class="sxs-lookup"><span data-stu-id="de2a2-105">This application does not demonstrate real world scenarios, such as using smart cards.</span></span> <span data-ttu-id="de2a2-106">Místo toho ukazuje základy šifrování a dešifrování.</span><span class="sxs-lookup"><span data-stu-id="de2a2-106">Instead, it demonstrates the fundamentals of encryption and decryption.</span></span>  
  
 <span data-ttu-id="de2a2-107">Tento návod používá pro šifrování následující pokyny:</span><span class="sxs-lookup"><span data-stu-id="de2a2-107">This walkthrough uses the following guidelines for encryption:</span></span>  
  
- <span data-ttu-id="de2a2-108">Použijte třídu, symetrický algoritmus pro šifrování a dešifrování dat pomocí automatického vygenerovaného <xref:System.Security.Cryptography.SymmetricAlgorithm.Key%2A> a <xref:System.Security.Cryptography.SymmetricAlgorithm.IV%2A>. <xref:System.Security.Cryptography.RijndaelManaged></span><span class="sxs-lookup"><span data-stu-id="de2a2-108">Use the <xref:System.Security.Cryptography.RijndaelManaged> class, a symmetric algorithm, to encrypt and decrypt data by using its automatically generated <xref:System.Security.Cryptography.SymmetricAlgorithm.Key%2A> and <xref:System.Security.Cryptography.SymmetricAlgorithm.IV%2A>.</span></span>  
  
- <span data-ttu-id="de2a2-109">Použijte asymetrický algoritmus pro šifrování a dešifrování klíče pro data zašifrovaná pomocí <xref:System.Security.Cryptography.RijndaelManaged>. <xref:System.Security.Cryptography.RSACryptoServiceProvider></span><span class="sxs-lookup"><span data-stu-id="de2a2-109">Use the <xref:System.Security.Cryptography.RSACryptoServiceProvider>, an asymmetric algorithm, to encrypt and decrypt the key to the data encrypted by <xref:System.Security.Cryptography.RijndaelManaged>.</span></span> <span data-ttu-id="de2a2-110">Asymetrické algoritmy se nejlépe používají pro menší objemy dat, jako je například klíč.</span><span class="sxs-lookup"><span data-stu-id="de2a2-110">Asymmetric algorithms are best used for smaller amounts of data, such as a key.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="de2a2-111">Chcete-li chránit data v počítači namísto výměny šifrovaného obsahu s jinými lidmi, zvažte použití <xref:System.Security.Cryptography.ProtectedData> tříd nebo. <xref:System.Security.Cryptography.ProtectedMemory></span><span class="sxs-lookup"><span data-stu-id="de2a2-111">If you want to protect data on your computer instead of exchanging encrypted content with other people, consider using the <xref:System.Security.Cryptography.ProtectedData> or <xref:System.Security.Cryptography.ProtectedMemory> classes.</span></span>  
  
 <span data-ttu-id="de2a2-112">Následující tabulka shrnuje kryptografické úlohy v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="de2a2-112">The following table summarizes the cryptographic tasks in this topic.</span></span>  
  
|<span data-ttu-id="de2a2-113">Úloha</span><span class="sxs-lookup"><span data-stu-id="de2a2-113">Task</span></span>|<span data-ttu-id="de2a2-114">Popis</span><span class="sxs-lookup"><span data-stu-id="de2a2-114">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="de2a2-115">Vytvoření aplikace model Windows Forms</span><span class="sxs-lookup"><span data-stu-id="de2a2-115">Creating a Windows Forms application</span></span>|<span data-ttu-id="de2a2-116">Seznam ovládacích prvků, které jsou požadovány ke spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="de2a2-116">Lists the controls that are required to run the application.</span></span>|  
|<span data-ttu-id="de2a2-117">Deklarace globálních objektů</span><span class="sxs-lookup"><span data-stu-id="de2a2-117">Declaring global objects</span></span>|<span data-ttu-id="de2a2-118">Deklaruje proměnné cesty <xref:System.Security.Cryptography.CspParameters> <xref:System.Security.Cryptography.RSACryptoServiceProvider> k řetězci, a a má globální kontext <xref:System.Windows.Forms.Form> třídy.</span><span class="sxs-lookup"><span data-stu-id="de2a2-118">Declares string path variables, the <xref:System.Security.Cryptography.CspParameters>, and the <xref:System.Security.Cryptography.RSACryptoServiceProvider> to have global context of the <xref:System.Windows.Forms.Form> class.</span></span>|  
|<span data-ttu-id="de2a2-119">Vytváření asymetrického klíče</span><span class="sxs-lookup"><span data-stu-id="de2a2-119">Creating an asymmetric key</span></span>|<span data-ttu-id="de2a2-120">Vytvoří asymetrickou dvojici hodnot veřejného a privátního klíče a přiřadí jí název kontejneru klíčů.</span><span class="sxs-lookup"><span data-stu-id="de2a2-120">Creates an asymmetric public and private key value pair and assigns it a key container name.</span></span>|  
|<span data-ttu-id="de2a2-121">Šifrování souboru</span><span class="sxs-lookup"><span data-stu-id="de2a2-121">Encrypting a file</span></span>|<span data-ttu-id="de2a2-122">Zobrazí dialogové okno pro výběr souboru pro šifrování a zašifruje soubor.</span><span class="sxs-lookup"><span data-stu-id="de2a2-122">Displays a dialog box to select a file for encryption and encrypts the file.</span></span>|  
|<span data-ttu-id="de2a2-123">Dešifrování souboru</span><span class="sxs-lookup"><span data-stu-id="de2a2-123">Decrypting a file</span></span>|<span data-ttu-id="de2a2-124">Zobrazí dialogové okno, ve kterém můžete vybrat zašifrovaný soubor pro dešifrování a dešifrovat soubor.</span><span class="sxs-lookup"><span data-stu-id="de2a2-124">Displays a dialog box to select an encrypted file for decryption and decrypts the file.</span></span>|  
|<span data-ttu-id="de2a2-125">Získání privátního klíče</span><span class="sxs-lookup"><span data-stu-id="de2a2-125">Getting a private key</span></span>|<span data-ttu-id="de2a2-126">Získá úplnou dvojici klíčů pomocí názvu kontejneru klíčů.</span><span class="sxs-lookup"><span data-stu-id="de2a2-126">Gets the full key pair using the key container name.</span></span>|  
|<span data-ttu-id="de2a2-127">Export veřejného klíče</span><span class="sxs-lookup"><span data-stu-id="de2a2-127">Exporting a public key</span></span>|<span data-ttu-id="de2a2-128">Uloží klíč do souboru XML s pouze veřejnými parametry.</span><span class="sxs-lookup"><span data-stu-id="de2a2-128">Saves the key to an XML file with only public parameters.</span></span>|  
|<span data-ttu-id="de2a2-129">Import veřejného klíče</span><span class="sxs-lookup"><span data-stu-id="de2a2-129">Importing a public key</span></span>|<span data-ttu-id="de2a2-130">Načte klíč ze souboru XML do kontejneru klíčů.</span><span class="sxs-lookup"><span data-stu-id="de2a2-130">Loads the key from an XML file into the key container.</span></span>|  
|<span data-ttu-id="de2a2-131">Testování aplikace</span><span class="sxs-lookup"><span data-stu-id="de2a2-131">Testing the application</span></span>|<span data-ttu-id="de2a2-132">Uvádí postupy pro testování této aplikace.</span><span class="sxs-lookup"><span data-stu-id="de2a2-132">Lists procedures for testing this application.</span></span>|  
  
## <a name="prerequisites"></a><span data-ttu-id="de2a2-133">Požadavky</span><span class="sxs-lookup"><span data-stu-id="de2a2-133">Prerequisites</span></span>  
 <span data-ttu-id="de2a2-134">K dokončení tohoto návodu budete potřebovat následující komponenty:</span><span class="sxs-lookup"><span data-stu-id="de2a2-134">You need the following components to complete this walkthrough:</span></span>  
  
- <span data-ttu-id="de2a2-135">Odkazy na <xref:System.IO> obory <xref:System.Security.Cryptography> názvů a.</span><span class="sxs-lookup"><span data-stu-id="de2a2-135">References to the <xref:System.IO> and <xref:System.Security.Cryptography> namespaces.</span></span>  
  
## <a name="creating-a-windows-forms-application"></a><span data-ttu-id="de2a2-136">Vytvoření aplikace model Windows Forms</span><span class="sxs-lookup"><span data-stu-id="de2a2-136">Creating a Windows Forms Application</span></span>  
 <span data-ttu-id="de2a2-137">Většina příkladů kódu v tomto návodu je navržena jako obslužné rutiny událostí pro ovládací prvky tlačítek.</span><span class="sxs-lookup"><span data-stu-id="de2a2-137">Most of the code examples in this walkthrough are designed to be event handlers for button controls.</span></span> <span data-ttu-id="de2a2-138">V následující tabulce jsou uvedeny ovládací prvky požadované pro ukázkovou aplikaci a jejich požadované názvy, aby odpovídaly příkladům kódu.</span><span class="sxs-lookup"><span data-stu-id="de2a2-138">The following table lists the controls required for the sample application and their required names to match the code examples.</span></span>  
  
|<span data-ttu-id="de2a2-139">Control</span><span class="sxs-lookup"><span data-stu-id="de2a2-139">Control</span></span>|<span data-ttu-id="de2a2-140">Name</span><span class="sxs-lookup"><span data-stu-id="de2a2-140">Name</span></span>|<span data-ttu-id="de2a2-141">Vlastnost text (podle potřeby)</span><span class="sxs-lookup"><span data-stu-id="de2a2-141">Text property (as needed)</span></span>|  
|-------------|----------|---------------------------------|  
|<xref:System.Windows.Forms.Button>|`buttonEncryptFile`|<span data-ttu-id="de2a2-142">Šifrovat soubor</span><span class="sxs-lookup"><span data-stu-id="de2a2-142">Encrypt File</span></span>|  
|<xref:System.Windows.Forms.Button>|`buttonDecryptFile`|<span data-ttu-id="de2a2-143">Dešifrovat soubor</span><span class="sxs-lookup"><span data-stu-id="de2a2-143">Decrypt File</span></span>|  
|<xref:System.Windows.Forms.Button>|`buttonCreateAsmKeys`|<span data-ttu-id="de2a2-144">Vytvořit klíče</span><span class="sxs-lookup"><span data-stu-id="de2a2-144">Create Keys</span></span>|  
|<xref:System.Windows.Forms.Button>|`buttonExportPublicKey`|<span data-ttu-id="de2a2-145">Exportovat veřejný klíč</span><span class="sxs-lookup"><span data-stu-id="de2a2-145">Export Public Key</span></span>|  
|<xref:System.Windows.Forms.Button>|`buttonImportPublicKey`|<span data-ttu-id="de2a2-146">Importovat veřejný klíč</span><span class="sxs-lookup"><span data-stu-id="de2a2-146">Import Public Key</span></span>|  
|<xref:System.Windows.Forms.Button>|`buttonGetPrivateKey`|<span data-ttu-id="de2a2-147">Získat privátní klíč</span><span class="sxs-lookup"><span data-stu-id="de2a2-147">Get Private Key</span></span>|  
|<xref:System.Windows.Forms.Label>|`label1`|<span data-ttu-id="de2a2-148">Klíč není nastaven.</span><span class="sxs-lookup"><span data-stu-id="de2a2-148">Key not set</span></span>|  
|<xref:System.Windows.Forms.OpenFileDialog>|`openFileDialog1`||  
|<xref:System.Windows.Forms.OpenFileDialog>|`openFileDialog2`||  
  
 <span data-ttu-id="de2a2-149">Dvojím kliknutím na tlačítka v návrháři sady Visual Studio vytvořte obslužné rutiny událostí.</span><span class="sxs-lookup"><span data-stu-id="de2a2-149">Double-click the buttons in the  Visual Studio designer to create their event handlers.</span></span>  
  
## <a name="declaring-global-objects"></a><span data-ttu-id="de2a2-150">Deklarace globálních objektů</span><span class="sxs-lookup"><span data-stu-id="de2a2-150">Declaring Global Objects</span></span>  
 <span data-ttu-id="de2a2-151">Do konstruktoru formuláře přidejte následující kód.</span><span class="sxs-lookup"><span data-stu-id="de2a2-151">Add the following code to the Form's constructor.</span></span> <span data-ttu-id="de2a2-152">Upravte řetězcové proměnné pro vaše prostředí a předvolby.</span><span class="sxs-lookup"><span data-stu-id="de2a2-152">Edit the string variables for your environment and preferences.</span></span>  
  
 [!code-csharp[CryptoWalkThru#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#1)]
 [!code-vb[CryptoWalkThru#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#1)]  
  
## <a name="creating-an-asymmetric-key"></a><span data-ttu-id="de2a2-153">Vytváření asymetrického klíče</span><span class="sxs-lookup"><span data-stu-id="de2a2-153">Creating an Asymmetric Key</span></span>  
 <span data-ttu-id="de2a2-154">Tato úloha vytvoří asymetrický klíč, který šifruje a dešifruje <xref:System.Security.Cryptography.RijndaelManaged> klíč.</span><span class="sxs-lookup"><span data-stu-id="de2a2-154">This task creates an asymmetric key that encrypts and decrypts the <xref:System.Security.Cryptography.RijndaelManaged> key.</span></span> <span data-ttu-id="de2a2-155">Tento klíč se použil k zašifrování obsahu a zobrazuje název kontejneru klíčů v ovládacím prvku popisek.</span><span class="sxs-lookup"><span data-stu-id="de2a2-155">This key was used to encrypt the content and it displays the key container name on the label control.</span></span>  
  
 <span data-ttu-id="de2a2-156">Přidejte následující kód jako `Click` obslužnou rutinu události `Create Keys` pro tlačítko (`buttonCreateAsmKeys_Click`).</span><span class="sxs-lookup"><span data-stu-id="de2a2-156">Add the following code as the `Click` event handler for the `Create Keys` button (`buttonCreateAsmKeys_Click`).</span></span>  
  
 [!code-csharp[CryptoWalkThru#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#2)]
 [!code-vb[CryptoWalkThru#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#2)]  
  
## <a name="encrypting-a-file"></a><span data-ttu-id="de2a2-157">Šifrování souboru</span><span class="sxs-lookup"><span data-stu-id="de2a2-157">Encrypting a File</span></span>  
 <span data-ttu-id="de2a2-158">Tato úloha zahrnuje dvě metody: metodu obslužné rutiny události pro `Encrypt File` tlačítko (`buttonEncryptFile_Click`) a `EncryptFile` metodu.</span><span class="sxs-lookup"><span data-stu-id="de2a2-158">This task involves two methods: the event handler method for the `Encrypt File` button (`buttonEncryptFile_Click`) and the `EncryptFile` method.</span></span> <span data-ttu-id="de2a2-159">První metoda zobrazí dialogové okno pro výběr souboru a předá název souboru druhé metodě, která provádí šifrování.</span><span class="sxs-lookup"><span data-stu-id="de2a2-159">The first method displays a dialog box for selecting a file and passes the file name to the second method, which performs the encryption.</span></span>  
  
 <span data-ttu-id="de2a2-160">Zašifrovaný obsah, klíč a IV jsou uloženy do jednoho <xref:System.IO.FileStream>, který je označován jako balíček šifrování.</span><span class="sxs-lookup"><span data-stu-id="de2a2-160">The encrypted content, key, and IV are all saved to one <xref:System.IO.FileStream>, which is referred to as the encryption package.</span></span>  
  
 <span data-ttu-id="de2a2-161">`EncryptFile` Metoda provede následující akce:</span><span class="sxs-lookup"><span data-stu-id="de2a2-161">The `EncryptFile` method does the following:</span></span>  
  
1. <span data-ttu-id="de2a2-162"><xref:System.Security.Cryptography.RijndaelManaged> Vytvoří symetrický algoritmus pro šifrování obsahu.</span><span class="sxs-lookup"><span data-stu-id="de2a2-162">Creates a <xref:System.Security.Cryptography.RijndaelManaged> symmetric algorithm to encrypt the content.</span></span>  
  
2. <span data-ttu-id="de2a2-163">Vytvoří objekt pro šifrování <xref:System.Security.Cryptography.RijndaelManaged>klíče. <xref:System.Security.Cryptography.RSACryptoServiceProvider></span><span class="sxs-lookup"><span data-stu-id="de2a2-163">Creates an <xref:System.Security.Cryptography.RSACryptoServiceProvider> object to encrypt the <xref:System.Security.Cryptography.RijndaelManaged> key.</span></span>  
  
3. <span data-ttu-id="de2a2-164">Používá objekt ke čtení a <xref:System.IO.FileStream> šifrování zdrojového souboru, v blocích bajtů, do cílového <xref:System.IO.FileStream> objektu pro zašifrovaný soubor. <xref:System.Security.Cryptography.CryptoStream></span><span class="sxs-lookup"><span data-stu-id="de2a2-164">Uses a <xref:System.Security.Cryptography.CryptoStream> object to read and encrypt the <xref:System.IO.FileStream> of the source file, in blocks of bytes, into a destination <xref:System.IO.FileStream> object for the encrypted file.</span></span>  
  
4. <span data-ttu-id="de2a2-165">Určuje délku šifrovaného klíče a IV a vytvoří pole bajtů jejich hodnot délky.</span><span class="sxs-lookup"><span data-stu-id="de2a2-165">Determines the lengths of the encrypted key and IV, and creates byte arrays of their length values.</span></span>  
  
5. <span data-ttu-id="de2a2-166">Zapíše klíč, IV a jejich hodnoty délky do šifrovaného balíčku.</span><span class="sxs-lookup"><span data-stu-id="de2a2-166">Writes the Key, IV, and their length values to the encrypted package.</span></span>  
  
 <span data-ttu-id="de2a2-167">Šifrovací balíček používá následující formát:</span><span class="sxs-lookup"><span data-stu-id="de2a2-167">The encryption package uses the following format:</span></span>  
  
- <span data-ttu-id="de2a2-168">Délka klíče, bajty 0-3</span><span class="sxs-lookup"><span data-stu-id="de2a2-168">Key length, bytes 0 - 3</span></span>  
  
- <span data-ttu-id="de2a2-169">Délka IV, bajty 4-7</span><span class="sxs-lookup"><span data-stu-id="de2a2-169">IV length, bytes 4 - 7</span></span>  
  
- <span data-ttu-id="de2a2-170">Šifrovaný klíč</span><span class="sxs-lookup"><span data-stu-id="de2a2-170">Encrypted key</span></span>  
  
- <span data-ttu-id="de2a2-171">IV</span><span class="sxs-lookup"><span data-stu-id="de2a2-171">IV</span></span>  
  
- <span data-ttu-id="de2a2-172">Šifrovaný text</span><span class="sxs-lookup"><span data-stu-id="de2a2-172">Cipher text</span></span>  
  
 <span data-ttu-id="de2a2-173">Délku klíče a IV můžete použít k určení počátečních bodů a délek všech částí šifrovacího balíčku, které pak můžete použít k dešifrování souboru.</span><span class="sxs-lookup"><span data-stu-id="de2a2-173">You can use the lengths of the key and IV to determine the starting points and lengths of all parts of the encryption package, which can then be used to decrypt the file.</span></span>  
  
 <span data-ttu-id="de2a2-174">Přidejte následující kód jako `Click` obslužnou rutinu události `Encrypt File` pro tlačítko (`buttonEncryptFile_Click`).</span><span class="sxs-lookup"><span data-stu-id="de2a2-174">Add the following code as the `Click` event handler for the `Encrypt File` button (`buttonEncryptFile_Click`).</span></span>  
  
 [!code-csharp[CryptoWalkThru#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#3)]
 [!code-vb[CryptoWalkThru#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#3)]  
  
 <span data-ttu-id="de2a2-175">Do formuláře přidejte `EncryptFile` následující metodu.</span><span class="sxs-lookup"><span data-stu-id="de2a2-175">Add the following `EncryptFile` method to the form.</span></span>  
  
 [!code-csharp[CryptoWalkThru#5](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#5)]
 [!code-vb[CryptoWalkThru#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#5)]  
  
## <a name="decrypting-a-file"></a><span data-ttu-id="de2a2-176">Dešifrování souboru</span><span class="sxs-lookup"><span data-stu-id="de2a2-176">Decrypting a File</span></span>  
 <span data-ttu-id="de2a2-177">Tato úloha zahrnuje dvě metody, metodu obslužné rutiny události pro `Decrypt File` tlačítko (`buttonDecryptFile_Click`) a `DecryptFile` metodu.</span><span class="sxs-lookup"><span data-stu-id="de2a2-177">This task involves two methods, the event handler method for the `Decrypt File` button (`buttonDecryptFile_Click`), and the `DecryptFile` method.</span></span> <span data-ttu-id="de2a2-178">První metoda zobrazí dialogové okno pro výběr souboru a předá jeho název souboru druhé metodě, která provádí dešifrování.</span><span class="sxs-lookup"><span data-stu-id="de2a2-178">The first method displays a dialog box for selecting a file and passes its file name to the second method, which performs the decryption.</span></span>  
  
 <span data-ttu-id="de2a2-179">`Decrypt` Metoda provede následující akce:</span><span class="sxs-lookup"><span data-stu-id="de2a2-179">The `Decrypt` method does the following:</span></span>  
  
1. <span data-ttu-id="de2a2-180"><xref:System.Security.Cryptography.RijndaelManaged> Vytvoří symetrický algoritmus pro dešifrování obsahu.</span><span class="sxs-lookup"><span data-stu-id="de2a2-180">Creates a <xref:System.Security.Cryptography.RijndaelManaged> symmetric algorithm to decrypt the content.</span></span>  
  
2. <span data-ttu-id="de2a2-181">Přečte prvních osm bajtů <xref:System.IO.FileStream> zašifrovaného balíčku do polí bajtů, aby získala délky šifrovaného klíče a IV.</span><span class="sxs-lookup"><span data-stu-id="de2a2-181">Reads the first eight bytes of the <xref:System.IO.FileStream> of the encrypted package into byte arrays to obtain the lengths of the encrypted key and the IV.</span></span>  
  
3. <span data-ttu-id="de2a2-182">Extrahuje klíč a IV z šifrovacího balíčku do polí bajtů.</span><span class="sxs-lookup"><span data-stu-id="de2a2-182">Extracts the key and IV from the encryption package into byte arrays.</span></span>  
  
4. <span data-ttu-id="de2a2-183">Vytvoří objekt pro dešifrování <xref:System.Security.Cryptography.RijndaelManaged>klíče. <xref:System.Security.Cryptography.RSACryptoServiceProvider></span><span class="sxs-lookup"><span data-stu-id="de2a2-183">Creates an <xref:System.Security.Cryptography.RSACryptoServiceProvider> object to decrypt the <xref:System.Security.Cryptography.RijndaelManaged> key.</span></span>  
  
5. <span data-ttu-id="de2a2-184">Používá objekt pro čtení a dešifrování oddílu <xref:System.IO.FileStream> šifry textu v balíčku šifrování v blocích bajtů do <xref:System.IO.FileStream> objektu pro dešifrovaný soubor. <xref:System.Security.Cryptography.CryptoStream></span><span class="sxs-lookup"><span data-stu-id="de2a2-184">Uses a <xref:System.Security.Cryptography.CryptoStream> object to read and decrypt the cipher text section of the <xref:System.IO.FileStream> encryption package, in blocks of bytes, into the <xref:System.IO.FileStream> object for the decrypted file.</span></span> <span data-ttu-id="de2a2-185">Po dokončení se dešifrování dokončí.</span><span class="sxs-lookup"><span data-stu-id="de2a2-185">When this is finished, the decryption is completed.</span></span>  
  
 <span data-ttu-id="de2a2-186">Přidejte následující kód jako `Click` obslužnou rutinu události `Decrypt File` pro tlačítko.</span><span class="sxs-lookup"><span data-stu-id="de2a2-186">Add the following code as the `Click` event handler for the `Decrypt File` button.</span></span>  
  
 [!code-csharp[CryptoWalkThru#4](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#4)]
 [!code-vb[CryptoWalkThru#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#4)]  
  
 <span data-ttu-id="de2a2-187">Do formuláře přidejte `DecryptFile` následující metodu.</span><span class="sxs-lookup"><span data-stu-id="de2a2-187">Add the following `DecryptFile` method to the form.</span></span>  
  
 [!code-csharp[CryptoWalkThru#6](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#6)]
 [!code-vb[CryptoWalkThru#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#6)]  
  
## <a name="exporting-a-public-key"></a><span data-ttu-id="de2a2-188">Export veřejného klíče</span><span class="sxs-lookup"><span data-stu-id="de2a2-188">Exporting a Public Key</span></span>  
 <span data-ttu-id="de2a2-189">Tento úkol uloží klíč vytvořený `Create Keys` tlačítkem do souboru.</span><span class="sxs-lookup"><span data-stu-id="de2a2-189">This task saves the key created by the `Create Keys` button to a file.</span></span> <span data-ttu-id="de2a2-190">Exportuje pouze veřejné parametry.</span><span class="sxs-lookup"><span data-stu-id="de2a2-190">It exports only the public parameters.</span></span>  
  
 <span data-ttu-id="de2a2-191">Tato úloha simuluje scénář Alice, která dává Bobovi veřejný klíč, aby k nim mohl šifrovat soubory.</span><span class="sxs-lookup"><span data-stu-id="de2a2-191">This task simulates the scenario of Alice giving Bob her public key so that he can encrypt files for her.</span></span> <span data-ttu-id="de2a2-192">A ostatní, kteří mají tento veřejný klíč, nebudou schopni je dešifrovat, protože nemají úplný pár klíčů s privátními parametry.</span><span class="sxs-lookup"><span data-stu-id="de2a2-192">He and others who have that public key will not be able to decrypt them because they do not have the full key pair with private parameters.</span></span>  
  
 <span data-ttu-id="de2a2-193">Přidejte následující kód jako `Click` obslužnou rutinu události `Export Public Key` pro tlačítko (`buttonExportPublicKey_Click`).</span><span class="sxs-lookup"><span data-stu-id="de2a2-193">Add the following code as the `Click` event handler for the `Export Public Key` button (`buttonExportPublicKey_Click`).</span></span>  
  
 [!code-csharp[CryptoWalkThru#8](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#8)]
 [!code-vb[CryptoWalkThru#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#8)]  
  
## <a name="importing-a-public-key"></a><span data-ttu-id="de2a2-194">Import veřejného klíče</span><span class="sxs-lookup"><span data-stu-id="de2a2-194">Importing a Public Key</span></span>  
 <span data-ttu-id="de2a2-195">Tato úloha načte klíč jenom s veřejnými parametry, jak je vytvořil `Export Public Key` tlačítko, a nastaví ho jako název kontejneru klíčů.</span><span class="sxs-lookup"><span data-stu-id="de2a2-195">This task loads the key with only public parameters, as created by the `Export Public Key` button, and sets it as the key container name.</span></span>  
  
 <span data-ttu-id="de2a2-196">Tato úloha simuluje scénář, který Bob načítá klíč Alice, jenom s veřejnými parametry, aby k nim mohl šifrovat soubory.</span><span class="sxs-lookup"><span data-stu-id="de2a2-196">This task simulates the scenario of Bob loading Alice's key with only public parameters so he can encrypt files for her.</span></span>  
  
 <span data-ttu-id="de2a2-197">Přidejte následující kód jako `Click` obslužnou rutinu události `Import Public Key` pro tlačítko (`buttonImportPublicKey_Click`).</span><span class="sxs-lookup"><span data-stu-id="de2a2-197">Add the following code as the `Click` event handler for the `Import Public Key` button (`buttonImportPublicKey_Click`).</span></span>  
  
 [!code-csharp[CryptoWalkThru#9](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#9)]
 [!code-vb[CryptoWalkThru#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#9)]  
  
## <a name="getting-a-private-key"></a><span data-ttu-id="de2a2-198">Získání privátního klíče</span><span class="sxs-lookup"><span data-stu-id="de2a2-198">Getting a Private Key</span></span>  
 <span data-ttu-id="de2a2-199">Tato úloha nastaví název kontejneru klíčů na název klíče vytvořeného pomocí `Create Keys` tlačítka.</span><span class="sxs-lookup"><span data-stu-id="de2a2-199">This task sets the key container name to the name of the key created by using the `Create Keys` button.</span></span> <span data-ttu-id="de2a2-200">Kontejner klíčů bude obsahovat úplný pár klíčů s privátními parametry.</span><span class="sxs-lookup"><span data-stu-id="de2a2-200">The key container will contain the full key pair with private parameters.</span></span>  
  
 <span data-ttu-id="de2a2-201">Tato úloha simuluje scénář Alice, který používá svůj privátní klíč k dešifrování souborů šifrovaných Bobem.</span><span class="sxs-lookup"><span data-stu-id="de2a2-201">This task simulates the scenario of Alice using her private key to decrypt files encrypted by Bob.</span></span>  
  
 <span data-ttu-id="de2a2-202">Přidejte následující kód jako `Click` obslužnou rutinu události `Get Private Key` pro tlačítko (`buttonGetPrivateKey_Click`).</span><span class="sxs-lookup"><span data-stu-id="de2a2-202">Add the following code as the `Click` event handler for the `Get Private Key` button (`buttonGetPrivateKey_Click`).</span></span>  
  
 [!code-csharp[CryptoWalkThru#7](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#7)]
 [!code-vb[CryptoWalkThru#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#7)]  
  
## <a name="testing-the-application"></a><span data-ttu-id="de2a2-203">Testování aplikace</span><span class="sxs-lookup"><span data-stu-id="de2a2-203">Testing the Application</span></span>  
 <span data-ttu-id="de2a2-204">Po vytvoření aplikace proveďte následující testovací scénáře.</span><span class="sxs-lookup"><span data-stu-id="de2a2-204">After you have built the application, perform the following testing scenarios.</span></span>  
  
#### <a name="to-create-keys-encrypt-and-decrypt"></a><span data-ttu-id="de2a2-205">Vytvoření klíčů, šifrování a dešifrování</span><span class="sxs-lookup"><span data-stu-id="de2a2-205">To create keys, encrypt, and decrypt</span></span>  
  
1. <span data-ttu-id="de2a2-206">Klikněte na `Create Keys` tlačítko.</span><span class="sxs-lookup"><span data-stu-id="de2a2-206">Click the `Create Keys` button.</span></span> <span data-ttu-id="de2a2-207">Popisek zobrazí název klíče a ukáže, že se jedná o úplný pár klíčů.</span><span class="sxs-lookup"><span data-stu-id="de2a2-207">The label displays the key name and shows that it is a full key pair.</span></span>  
  
2. <span data-ttu-id="de2a2-208">Klikněte na `Export Public Key` tlačítko.</span><span class="sxs-lookup"><span data-stu-id="de2a2-208">Click the `Export Public Key` button.</span></span> <span data-ttu-id="de2a2-209">Všimněte si, že export parametrů veřejného klíče nemění aktuální klíč.</span><span class="sxs-lookup"><span data-stu-id="de2a2-209">Note that exporting the public key parameters does not change the current key.</span></span>  
  
3. <span data-ttu-id="de2a2-210">Klikněte na `Encrypt File` tlačítko a vyberte soubor.</span><span class="sxs-lookup"><span data-stu-id="de2a2-210">Click the `Encrypt File` button and select a file.</span></span>  
  
4. <span data-ttu-id="de2a2-211">Klikněte na `Decrypt File` tlačítko a vyberte soubor právě zašifrovaný.</span><span class="sxs-lookup"><span data-stu-id="de2a2-211">Click the `Decrypt File` button and select the file just encrypted.</span></span>  
  
5. <span data-ttu-id="de2a2-212">Prověřte soubor, který se právě dešifroval.</span><span class="sxs-lookup"><span data-stu-id="de2a2-212">Examine the file just decrypted.</span></span>  
  
6. <span data-ttu-id="de2a2-213">Zavřete aplikaci a restartujte ji, abyste v dalším scénáři otestovali načtení trvalých kontejnerů klíčů.</span><span class="sxs-lookup"><span data-stu-id="de2a2-213">Close the application and restart it to test retrieving persisted key containers in the next scenario.</span></span>  
  
#### <a name="to-encrypt-using-the-public-key"></a><span data-ttu-id="de2a2-214">Šifrování pomocí veřejného klíče</span><span class="sxs-lookup"><span data-stu-id="de2a2-214">To encrypt using the public key</span></span>  
  
1. <span data-ttu-id="de2a2-215">Klikněte na `Import Public Key` tlačítko.</span><span class="sxs-lookup"><span data-stu-id="de2a2-215">Click the `Import Public Key` button.</span></span> <span data-ttu-id="de2a2-216">Popisek zobrazí název klíče a ukáže, že je pouze veřejný.</span><span class="sxs-lookup"><span data-stu-id="de2a2-216">The label displays the key name and shows that it is public only.</span></span>  
  
2. <span data-ttu-id="de2a2-217">Klikněte na `Encrypt File` tlačítko a vyberte soubor.</span><span class="sxs-lookup"><span data-stu-id="de2a2-217">Click the `Encrypt File` button and select a file.</span></span>  
  
3. <span data-ttu-id="de2a2-218">Klikněte na `Decrypt File` tlačítko a vyberte soubor právě zašifrovaný.</span><span class="sxs-lookup"><span data-stu-id="de2a2-218">Click the `Decrypt File` button and select the file just encrypted.</span></span> <span data-ttu-id="de2a2-219">To se nezdaří, protože musíte mít privátní klíč k dešifrování.</span><span class="sxs-lookup"><span data-stu-id="de2a2-219">This will fail because you must have the private key to decrypt.</span></span>  
  
 <span data-ttu-id="de2a2-220">Tento scénář ukazuje pouze veřejný klíč k šifrování souboru pro jinou osobu.</span><span class="sxs-lookup"><span data-stu-id="de2a2-220">This scenario demonstrates having only the public key to encrypt a file for another person.</span></span> <span data-ttu-id="de2a2-221">Obvykle vám někdo poskytne jenom veřejný klíč a odpírá privátní klíč k dešifrování.</span><span class="sxs-lookup"><span data-stu-id="de2a2-221">Typically that person would give you only the public key and withhold the private key for decryption.</span></span>  
  
#### <a name="to-decrypt-using-the-private-key"></a><span data-ttu-id="de2a2-222">Dešifrování pomocí privátního klíče</span><span class="sxs-lookup"><span data-stu-id="de2a2-222">To decrypt using the private key</span></span>  
  
1. <span data-ttu-id="de2a2-223">Klikněte na `Get Private Key` tlačítko.</span><span class="sxs-lookup"><span data-stu-id="de2a2-223">Click the `Get Private Key` button.</span></span> <span data-ttu-id="de2a2-224">Popisek zobrazí název klíče a ukáže, zda se jedná o úplný pár klíčů.</span><span class="sxs-lookup"><span data-stu-id="de2a2-224">The label displays the key name and shows whether it is the full key pair.</span></span>  
  
2. <span data-ttu-id="de2a2-225">Klikněte na `Decrypt File` tlačítko a vyberte soubor právě zašifrovaný.</span><span class="sxs-lookup"><span data-stu-id="de2a2-225">Click the `Decrypt File` button and select the file just encrypted.</span></span> <span data-ttu-id="de2a2-226">Tato akce bude úspěšná, protože máte úplný pár klíčů k dešifrování.</span><span class="sxs-lookup"><span data-stu-id="de2a2-226">This will be successful because you have the full key pair to decrypt.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de2a2-227">Viz také:</span><span class="sxs-lookup"><span data-stu-id="de2a2-227">See also</span></span>

- [<span data-ttu-id="de2a2-228">Kryptografické služby</span><span class="sxs-lookup"><span data-stu-id="de2a2-228">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)
