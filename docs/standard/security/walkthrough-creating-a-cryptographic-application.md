---
title: 'Návod: Vytvoření šifrovací aplikace'
description: Projděte si vytváření kryptografických aplikací. Naučte se šifrovat a dešifrovat obsah v model Windows Forms aplikaci.
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
ms.openlocfilehash: 72116227fbec2435d428ad2bbdb4cc74e5c3663f
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602177"
---
# <a name="walkthrough-creating-a-cryptographic-application"></a><span data-ttu-id="8de65-104">Návod: Vytvoření šifrovací aplikace</span><span class="sxs-lookup"><span data-stu-id="8de65-104">Walkthrough: Creating a Cryptographic Application</span></span>
<span data-ttu-id="8de65-105">Tento návod ukazuje, jak šifrovat a dešifrovat obsah.</span><span class="sxs-lookup"><span data-stu-id="8de65-105">This walkthrough demonstrates how to encrypt and decrypt content.</span></span> <span data-ttu-id="8de65-106">Příklady kódu jsou určeny pro model Windows Forms aplikace.</span><span class="sxs-lookup"><span data-stu-id="8de65-106">The code examples are designed for a Windows Forms application.</span></span> <span data-ttu-id="8de65-107">Tato aplikace nemonstruje scénáře reálného světa, jako je například použití čipových karet.</span><span class="sxs-lookup"><span data-stu-id="8de65-107">This application does not demonstrate real world scenarios, such as using smart cards.</span></span> <span data-ttu-id="8de65-108">Místo toho ukazuje základy šifrování a dešifrování.</span><span class="sxs-lookup"><span data-stu-id="8de65-108">Instead, it demonstrates the fundamentals of encryption and decryption.</span></span>  
  
 <span data-ttu-id="8de65-109">Tento návod používá pro šifrování následující pokyny:</span><span class="sxs-lookup"><span data-stu-id="8de65-109">This walkthrough uses the following guidelines for encryption:</span></span>  
  
- <span data-ttu-id="8de65-110">Použijte <xref:System.Security.Cryptography.RijndaelManaged> třídu, symetrický algoritmus pro šifrování a dešifrování dat pomocí automatického vygenerovaného <xref:System.Security.Cryptography.SymmetricAlgorithm.Key%2A> a <xref:System.Security.Cryptography.SymmetricAlgorithm.IV%2A> .</span><span class="sxs-lookup"><span data-stu-id="8de65-110">Use the <xref:System.Security.Cryptography.RijndaelManaged> class, a symmetric algorithm, to encrypt and decrypt data by using its automatically generated <xref:System.Security.Cryptography.SymmetricAlgorithm.Key%2A> and <xref:System.Security.Cryptography.SymmetricAlgorithm.IV%2A>.</span></span>  
  
- <span data-ttu-id="8de65-111">Použijte <xref:System.Security.Cryptography.RSACryptoServiceProvider> asymetrický algoritmus pro šifrování a dešifrování klíče pro data zašifrovaná pomocí <xref:System.Security.Cryptography.RijndaelManaged> .</span><span class="sxs-lookup"><span data-stu-id="8de65-111">Use the <xref:System.Security.Cryptography.RSACryptoServiceProvider>, an asymmetric algorithm, to encrypt and decrypt the key to the data encrypted by <xref:System.Security.Cryptography.RijndaelManaged>.</span></span> <span data-ttu-id="8de65-112">Asymetrické algoritmy se nejlépe používají pro menší objemy dat, jako je například klíč.</span><span class="sxs-lookup"><span data-stu-id="8de65-112">Asymmetric algorithms are best used for smaller amounts of data, such as a key.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="8de65-113">Chcete-li chránit data v počítači namísto výměny šifrovaného obsahu s jinými lidmi, zvažte použití <xref:System.Security.Cryptography.ProtectedData> <xref:System.Security.Cryptography.ProtectedMemory> tříd nebo.</span><span class="sxs-lookup"><span data-stu-id="8de65-113">If you want to protect data on your computer instead of exchanging encrypted content with other people, consider using the <xref:System.Security.Cryptography.ProtectedData> or <xref:System.Security.Cryptography.ProtectedMemory> classes.</span></span>  
  
 <span data-ttu-id="8de65-114">Následující tabulka shrnuje kryptografické úlohy v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="8de65-114">The following table summarizes the cryptographic tasks in this topic.</span></span>  
  
|<span data-ttu-id="8de65-115">Úkol</span><span class="sxs-lookup"><span data-stu-id="8de65-115">Task</span></span>|<span data-ttu-id="8de65-116">Popis</span><span class="sxs-lookup"><span data-stu-id="8de65-116">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="8de65-117">Vytvoření aplikace model Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8de65-117">Creating a Windows Forms application</span></span>|<span data-ttu-id="8de65-118">Seznam ovládacích prvků, které jsou požadovány ke spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="8de65-118">Lists the controls that are required to run the application.</span></span>|  
|<span data-ttu-id="8de65-119">Deklarace globálních objektů</span><span class="sxs-lookup"><span data-stu-id="8de65-119">Declaring global objects</span></span>|<span data-ttu-id="8de65-120">Deklaruje proměnné cesty k řetězci, <xref:System.Security.Cryptography.CspParameters> a a má <xref:System.Security.Cryptography.RSACryptoServiceProvider> globální kontext <xref:System.Windows.Forms.Form> třídy.</span><span class="sxs-lookup"><span data-stu-id="8de65-120">Declares string path variables, the <xref:System.Security.Cryptography.CspParameters>, and the <xref:System.Security.Cryptography.RSACryptoServiceProvider> to have global context of the <xref:System.Windows.Forms.Form> class.</span></span>|  
|<span data-ttu-id="8de65-121">Vytváření asymetrického klíče</span><span class="sxs-lookup"><span data-stu-id="8de65-121">Creating an asymmetric key</span></span>|<span data-ttu-id="8de65-122">Vytvoří asymetrickou dvojici hodnot veřejného a privátního klíče a přiřadí jí název kontejneru klíčů.</span><span class="sxs-lookup"><span data-stu-id="8de65-122">Creates an asymmetric public and private key value pair and assigns it a key container name.</span></span>|  
|<span data-ttu-id="8de65-123">Šifrování souboru</span><span class="sxs-lookup"><span data-stu-id="8de65-123">Encrypting a file</span></span>|<span data-ttu-id="8de65-124">Zobrazí dialogové okno pro výběr souboru pro šifrování a zašifruje soubor.</span><span class="sxs-lookup"><span data-stu-id="8de65-124">Displays a dialog box to select a file for encryption and encrypts the file.</span></span>|  
|<span data-ttu-id="8de65-125">Dešifrování souboru</span><span class="sxs-lookup"><span data-stu-id="8de65-125">Decrypting a file</span></span>|<span data-ttu-id="8de65-126">Zobrazí dialogové okno, ve kterém můžete vybrat zašifrovaný soubor pro dešifrování a dešifrovat soubor.</span><span class="sxs-lookup"><span data-stu-id="8de65-126">Displays a dialog box to select an encrypted file for decryption and decrypts the file.</span></span>|  
|<span data-ttu-id="8de65-127">Získání privátního klíče</span><span class="sxs-lookup"><span data-stu-id="8de65-127">Getting a private key</span></span>|<span data-ttu-id="8de65-128">Získá úplnou dvojici klíčů pomocí názvu kontejneru klíčů.</span><span class="sxs-lookup"><span data-stu-id="8de65-128">Gets the full key pair using the key container name.</span></span>|  
|<span data-ttu-id="8de65-129">Export veřejného klíče</span><span class="sxs-lookup"><span data-stu-id="8de65-129">Exporting a public key</span></span>|<span data-ttu-id="8de65-130">Uloží klíč do souboru XML s pouze veřejnými parametry.</span><span class="sxs-lookup"><span data-stu-id="8de65-130">Saves the key to an XML file with only public parameters.</span></span>|  
|<span data-ttu-id="8de65-131">Import veřejného klíče</span><span class="sxs-lookup"><span data-stu-id="8de65-131">Importing a public key</span></span>|<span data-ttu-id="8de65-132">Načte klíč ze souboru XML do kontejneru klíčů.</span><span class="sxs-lookup"><span data-stu-id="8de65-132">Loads the key from an XML file into the key container.</span></span>|  
|<span data-ttu-id="8de65-133">Testování aplikace</span><span class="sxs-lookup"><span data-stu-id="8de65-133">Testing the application</span></span>|<span data-ttu-id="8de65-134">Uvádí postupy pro testování této aplikace.</span><span class="sxs-lookup"><span data-stu-id="8de65-134">Lists procedures for testing this application.</span></span>|  
  
## <a name="prerequisites"></a><span data-ttu-id="8de65-135">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8de65-135">Prerequisites</span></span>  
 <span data-ttu-id="8de65-136">K dokončení tohoto návodu budete potřebovat následující komponenty:</span><span class="sxs-lookup"><span data-stu-id="8de65-136">You need the following components to complete this walkthrough:</span></span>  
  
- <span data-ttu-id="8de65-137">Odkazy na <xref:System.IO> <xref:System.Security.Cryptography> obory názvů a.</span><span class="sxs-lookup"><span data-stu-id="8de65-137">References to the <xref:System.IO> and <xref:System.Security.Cryptography> namespaces.</span></span>  
  
## <a name="creating-a-windows-forms-application"></a><span data-ttu-id="8de65-138">Vytvoření aplikace model Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8de65-138">Creating a Windows Forms Application</span></span>  
 <span data-ttu-id="8de65-139">Většina příkladů kódu v tomto návodu je navržena jako obslužné rutiny událostí pro ovládací prvky tlačítek.</span><span class="sxs-lookup"><span data-stu-id="8de65-139">Most of the code examples in this walkthrough are designed to be event handlers for button controls.</span></span> <span data-ttu-id="8de65-140">V následující tabulce jsou uvedeny ovládací prvky požadované pro ukázkovou aplikaci a jejich požadované názvy, aby odpovídaly příkladům kódu.</span><span class="sxs-lookup"><span data-stu-id="8de65-140">The following table lists the controls required for the sample application and their required names to match the code examples.</span></span>  
  
|<span data-ttu-id="8de65-141">Řízení</span><span class="sxs-lookup"><span data-stu-id="8de65-141">Control</span></span>|<span data-ttu-id="8de65-142">Name</span><span class="sxs-lookup"><span data-stu-id="8de65-142">Name</span></span>|<span data-ttu-id="8de65-143">Vlastnost text (podle potřeby)</span><span class="sxs-lookup"><span data-stu-id="8de65-143">Text property (as needed)</span></span>|  
|-------------|----------|---------------------------------|  
|<xref:System.Windows.Forms.Button>|`buttonEncryptFile`|<span data-ttu-id="8de65-144">Šifrovat soubor</span><span class="sxs-lookup"><span data-stu-id="8de65-144">Encrypt File</span></span>|  
|<xref:System.Windows.Forms.Button>|`buttonDecryptFile`|<span data-ttu-id="8de65-145">Dešifrovat soubor</span><span class="sxs-lookup"><span data-stu-id="8de65-145">Decrypt File</span></span>|  
|<xref:System.Windows.Forms.Button>|`buttonCreateAsmKeys`|<span data-ttu-id="8de65-146">Vytvořit klíče</span><span class="sxs-lookup"><span data-stu-id="8de65-146">Create Keys</span></span>|  
|<xref:System.Windows.Forms.Button>|`buttonExportPublicKey`|<span data-ttu-id="8de65-147">Exportovat veřejný klíč</span><span class="sxs-lookup"><span data-stu-id="8de65-147">Export Public Key</span></span>|  
|<xref:System.Windows.Forms.Button>|`buttonImportPublicKey`|<span data-ttu-id="8de65-148">Importovat veřejný klíč</span><span class="sxs-lookup"><span data-stu-id="8de65-148">Import Public Key</span></span>|  
|<xref:System.Windows.Forms.Button>|`buttonGetPrivateKey`|<span data-ttu-id="8de65-149">Získat privátní klíč</span><span class="sxs-lookup"><span data-stu-id="8de65-149">Get Private Key</span></span>|  
|<xref:System.Windows.Forms.Label>|`label1`|<span data-ttu-id="8de65-150">Klíč není nastaven.</span><span class="sxs-lookup"><span data-stu-id="8de65-150">Key not set</span></span>|  
|<xref:System.Windows.Forms.OpenFileDialog>|`openFileDialog1`||  
|<xref:System.Windows.Forms.OpenFileDialog>|`openFileDialog2`||  
  
 <span data-ttu-id="8de65-151">Dvojím kliknutím na tlačítka v návrháři sady Visual Studio vytvořte obslužné rutiny událostí.</span><span class="sxs-lookup"><span data-stu-id="8de65-151">Double-click the buttons in the  Visual Studio designer to create their event handlers.</span></span>  
  
## <a name="declaring-global-objects"></a><span data-ttu-id="8de65-152">Deklarace globálních objektů</span><span class="sxs-lookup"><span data-stu-id="8de65-152">Declaring Global Objects</span></span>  
 <span data-ttu-id="8de65-153">Do konstruktoru formuláře přidejte následující kód.</span><span class="sxs-lookup"><span data-stu-id="8de65-153">Add the following code to the Form's constructor.</span></span> <span data-ttu-id="8de65-154">Upravte řetězcové proměnné pro vaše prostředí a předvolby.</span><span class="sxs-lookup"><span data-stu-id="8de65-154">Edit the string variables for your environment and preferences.</span></span>  
  
 [!code-csharp[CryptoWalkThru#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#1)]
 [!code-vb[CryptoWalkThru#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#1)]  
  
## <a name="creating-an-asymmetric-key"></a><span data-ttu-id="8de65-155">Vytváření asymetrického klíče</span><span class="sxs-lookup"><span data-stu-id="8de65-155">Creating an Asymmetric Key</span></span>  
 <span data-ttu-id="8de65-156">Tato úloha vytvoří asymetrický klíč, který šifruje a dešifruje <xref:System.Security.Cryptography.RijndaelManaged> klíč.</span><span class="sxs-lookup"><span data-stu-id="8de65-156">This task creates an asymmetric key that encrypts and decrypts the <xref:System.Security.Cryptography.RijndaelManaged> key.</span></span> <span data-ttu-id="8de65-157">Tento klíč se použil k zašifrování obsahu a zobrazuje název kontejneru klíčů v ovládacím prvku popisek.</span><span class="sxs-lookup"><span data-stu-id="8de65-157">This key was used to encrypt the content and it displays the key container name on the label control.</span></span>  
  
 <span data-ttu-id="8de65-158">Přidejte následující kód jako `Click` obslužnou rutinu události pro `Create Keys` tlačítko ( `buttonCreateAsmKeys_Click` ).</span><span class="sxs-lookup"><span data-stu-id="8de65-158">Add the following code as the `Click` event handler for the `Create Keys` button (`buttonCreateAsmKeys_Click`).</span></span>  
  
 [!code-csharp[CryptoWalkThru#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#2)]
 [!code-vb[CryptoWalkThru#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#2)]  
  
## <a name="encrypting-a-file"></a><span data-ttu-id="8de65-159">Šifrování souboru</span><span class="sxs-lookup"><span data-stu-id="8de65-159">Encrypting a File</span></span>  
 <span data-ttu-id="8de65-160">Tato úloha zahrnuje dvě metody: metodu obslužné rutiny události pro `Encrypt File` tlačítko ( `buttonEncryptFile_Click` ) a `EncryptFile` metodu.</span><span class="sxs-lookup"><span data-stu-id="8de65-160">This task involves two methods: the event handler method for the `Encrypt File` button (`buttonEncryptFile_Click`) and the `EncryptFile` method.</span></span> <span data-ttu-id="8de65-161">První metoda zobrazí dialogové okno pro výběr souboru a předá název souboru druhé metodě, která provádí šifrování.</span><span class="sxs-lookup"><span data-stu-id="8de65-161">The first method displays a dialog box for selecting a file and passes the file name to the second method, which performs the encryption.</span></span>  
  
 <span data-ttu-id="8de65-162">Zašifrovaný obsah, klíč a IV jsou uloženy do jednoho <xref:System.IO.FileStream> , který je označován jako balíček šifrování.</span><span class="sxs-lookup"><span data-stu-id="8de65-162">The encrypted content, key, and IV are all saved to one <xref:System.IO.FileStream>, which is referred to as the encryption package.</span></span>  
  
 <span data-ttu-id="8de65-163">`EncryptFile`Metoda provede následující akce:</span><span class="sxs-lookup"><span data-stu-id="8de65-163">The `EncryptFile` method does the following:</span></span>  
  
1. <span data-ttu-id="8de65-164">Vytvoří <xref:System.Security.Cryptography.RijndaelManaged> symetrický algoritmus pro šifrování obsahu.</span><span class="sxs-lookup"><span data-stu-id="8de65-164">Creates a <xref:System.Security.Cryptography.RijndaelManaged> symmetric algorithm to encrypt the content.</span></span>  
  
2. <span data-ttu-id="8de65-165">Vytvoří <xref:System.Security.Cryptography.RSACryptoServiceProvider> objekt pro šifrování <xref:System.Security.Cryptography.RijndaelManaged> klíče.</span><span class="sxs-lookup"><span data-stu-id="8de65-165">Creates an <xref:System.Security.Cryptography.RSACryptoServiceProvider> object to encrypt the <xref:System.Security.Cryptography.RijndaelManaged> key.</span></span>  
  
3. <span data-ttu-id="8de65-166">Používá <xref:System.Security.Cryptography.CryptoStream> objekt ke čtení a šifrování <xref:System.IO.FileStream> zdrojového souboru, v blocích bajtů, do cílového <xref:System.IO.FileStream> objektu pro zašifrovaný soubor.</span><span class="sxs-lookup"><span data-stu-id="8de65-166">Uses a <xref:System.Security.Cryptography.CryptoStream> object to read and encrypt the <xref:System.IO.FileStream> of the source file, in blocks of bytes, into a destination <xref:System.IO.FileStream> object for the encrypted file.</span></span>  
  
4. <span data-ttu-id="8de65-167">Určuje délku šifrovaného klíče a IV a vytvoří pole bajtů jejich hodnot délky.</span><span class="sxs-lookup"><span data-stu-id="8de65-167">Determines the lengths of the encrypted key and IV, and creates byte arrays of their length values.</span></span>  
  
5. <span data-ttu-id="8de65-168">Zapíše klíč, IV a jejich hodnoty délky do šifrovaného balíčku.</span><span class="sxs-lookup"><span data-stu-id="8de65-168">Writes the Key, IV, and their length values to the encrypted package.</span></span>  
  
 <span data-ttu-id="8de65-169">Šifrovací balíček používá následující formát:</span><span class="sxs-lookup"><span data-stu-id="8de65-169">The encryption package uses the following format:</span></span>  
  
- <span data-ttu-id="8de65-170">Délka klíče, bajty 0-3</span><span class="sxs-lookup"><span data-stu-id="8de65-170">Key length, bytes 0 - 3</span></span>  
  
- <span data-ttu-id="8de65-171">Délka IV, bajty 4-7</span><span class="sxs-lookup"><span data-stu-id="8de65-171">IV length, bytes 4 - 7</span></span>  
  
- <span data-ttu-id="8de65-172">Šifrovaný klíč</span><span class="sxs-lookup"><span data-stu-id="8de65-172">Encrypted key</span></span>  
  
- <span data-ttu-id="8de65-173">IV</span><span class="sxs-lookup"><span data-stu-id="8de65-173">IV</span></span>  
  
- <span data-ttu-id="8de65-174">Šifrovaný text</span><span class="sxs-lookup"><span data-stu-id="8de65-174">Cipher text</span></span>  
  
 <span data-ttu-id="8de65-175">Délku klíče a IV můžete použít k určení počátečních bodů a délek všech částí šifrovacího balíčku, které pak můžete použít k dešifrování souboru.</span><span class="sxs-lookup"><span data-stu-id="8de65-175">You can use the lengths of the key and IV to determine the starting points and lengths of all parts of the encryption package, which can then be used to decrypt the file.</span></span>  
  
 <span data-ttu-id="8de65-176">Přidejte následující kód jako `Click` obslužnou rutinu události pro `Encrypt File` tlačítko ( `buttonEncryptFile_Click` ).</span><span class="sxs-lookup"><span data-stu-id="8de65-176">Add the following code as the `Click` event handler for the `Encrypt File` button (`buttonEncryptFile_Click`).</span></span>  
  
 [!code-csharp[CryptoWalkThru#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#3)]
 [!code-vb[CryptoWalkThru#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#3)]  
  
 <span data-ttu-id="8de65-177">`EncryptFile`Do formuláře přidejte následující metodu.</span><span class="sxs-lookup"><span data-stu-id="8de65-177">Add the following `EncryptFile` method to the form.</span></span>  
  
 [!code-csharp[CryptoWalkThru#5](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#5)]
 [!code-vb[CryptoWalkThru#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#5)]  
  
## <a name="decrypting-a-file"></a><span data-ttu-id="8de65-178">Dešifrování souboru</span><span class="sxs-lookup"><span data-stu-id="8de65-178">Decrypting a File</span></span>  
 <span data-ttu-id="8de65-179">Tato úloha zahrnuje dvě metody, metodu obslužné rutiny události pro `Decrypt File` tlačítko ( `buttonDecryptFile_Click` ) a `DecryptFile` metodu.</span><span class="sxs-lookup"><span data-stu-id="8de65-179">This task involves two methods, the event handler method for the `Decrypt File` button (`buttonDecryptFile_Click`), and the `DecryptFile` method.</span></span> <span data-ttu-id="8de65-180">První metoda zobrazí dialogové okno pro výběr souboru a předá jeho název souboru druhé metodě, která provádí dešifrování.</span><span class="sxs-lookup"><span data-stu-id="8de65-180">The first method displays a dialog box for selecting a file and passes its file name to the second method, which performs the decryption.</span></span>  
  
 <span data-ttu-id="8de65-181">`Decrypt`Metoda provede následující akce:</span><span class="sxs-lookup"><span data-stu-id="8de65-181">The `Decrypt` method does the following:</span></span>  
  
1. <span data-ttu-id="8de65-182">Vytvoří <xref:System.Security.Cryptography.RijndaelManaged> symetrický algoritmus pro dešifrování obsahu.</span><span class="sxs-lookup"><span data-stu-id="8de65-182">Creates a <xref:System.Security.Cryptography.RijndaelManaged> symmetric algorithm to decrypt the content.</span></span>  
  
2. <span data-ttu-id="8de65-183">Přečte prvních osm bajtů <xref:System.IO.FileStream> zašifrovaného balíčku do polí bajtů, aby získala délky šifrovaného klíče a IV.</span><span class="sxs-lookup"><span data-stu-id="8de65-183">Reads the first eight bytes of the <xref:System.IO.FileStream> of the encrypted package into byte arrays to obtain the lengths of the encrypted key and the IV.</span></span>  
  
3. <span data-ttu-id="8de65-184">Extrahuje klíč a IV z šifrovacího balíčku do polí bajtů.</span><span class="sxs-lookup"><span data-stu-id="8de65-184">Extracts the key and IV from the encryption package into byte arrays.</span></span>  
  
4. <span data-ttu-id="8de65-185">Vytvoří <xref:System.Security.Cryptography.RSACryptoServiceProvider> objekt pro dešifrování <xref:System.Security.Cryptography.RijndaelManaged> klíče.</span><span class="sxs-lookup"><span data-stu-id="8de65-185">Creates an <xref:System.Security.Cryptography.RSACryptoServiceProvider> object to decrypt the <xref:System.Security.Cryptography.RijndaelManaged> key.</span></span>  
  
5. <span data-ttu-id="8de65-186">Používá <xref:System.Security.Cryptography.CryptoStream> objekt pro čtení a dešifrování oddílu šifry textu <xref:System.IO.FileStream> v balíčku šifrování v blocích bajtů do <xref:System.IO.FileStream> objektu pro dešifrovaný soubor.</span><span class="sxs-lookup"><span data-stu-id="8de65-186">Uses a <xref:System.Security.Cryptography.CryptoStream> object to read and decrypt the cipher text section of the <xref:System.IO.FileStream> encryption package, in blocks of bytes, into the <xref:System.IO.FileStream> object for the decrypted file.</span></span> <span data-ttu-id="8de65-187">Po dokončení se dešifrování dokončí.</span><span class="sxs-lookup"><span data-stu-id="8de65-187">When this is finished, the decryption is completed.</span></span>  
  
 <span data-ttu-id="8de65-188">Přidejte následující kód jako `Click` obslužnou rutinu události pro `Decrypt File` tlačítko.</span><span class="sxs-lookup"><span data-stu-id="8de65-188">Add the following code as the `Click` event handler for the `Decrypt File` button.</span></span>  
  
 [!code-csharp[CryptoWalkThru#4](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#4)]
 [!code-vb[CryptoWalkThru#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#4)]  
  
 <span data-ttu-id="8de65-189">`DecryptFile`Do formuláře přidejte následující metodu.</span><span class="sxs-lookup"><span data-stu-id="8de65-189">Add the following `DecryptFile` method to the form.</span></span>  
  
 [!code-csharp[CryptoWalkThru#6](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#6)]
 [!code-vb[CryptoWalkThru#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#6)]  
  
## <a name="exporting-a-public-key"></a><span data-ttu-id="8de65-190">Export veřejného klíče</span><span class="sxs-lookup"><span data-stu-id="8de65-190">Exporting a Public Key</span></span>  
 <span data-ttu-id="8de65-191">Tento úkol uloží klíč vytvořený `Create Keys` tlačítkem do souboru.</span><span class="sxs-lookup"><span data-stu-id="8de65-191">This task saves the key created by the `Create Keys` button to a file.</span></span> <span data-ttu-id="8de65-192">Exportuje pouze veřejné parametry.</span><span class="sxs-lookup"><span data-stu-id="8de65-192">It exports only the public parameters.</span></span>  
  
 <span data-ttu-id="8de65-193">Tato úloha simuluje scénář Alice, která dává Bobovi veřejný klíč, aby k nim mohl šifrovat soubory.</span><span class="sxs-lookup"><span data-stu-id="8de65-193">This task simulates the scenario of Alice giving Bob her public key so that he can encrypt files for her.</span></span> <span data-ttu-id="8de65-194">A ostatní, kteří mají tento veřejný klíč, nebudou schopni je dešifrovat, protože nemají úplný pár klíčů s privátními parametry.</span><span class="sxs-lookup"><span data-stu-id="8de65-194">He and others who have that public key will not be able to decrypt them because they do not have the full key pair with private parameters.</span></span>  
  
 <span data-ttu-id="8de65-195">Přidejte následující kód jako `Click` obslužnou rutinu události pro `Export Public Key` tlačítko ( `buttonExportPublicKey_Click` ).</span><span class="sxs-lookup"><span data-stu-id="8de65-195">Add the following code as the `Click` event handler for the `Export Public Key` button (`buttonExportPublicKey_Click`).</span></span>  
  
 [!code-csharp[CryptoWalkThru#8](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#8)]
 [!code-vb[CryptoWalkThru#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#8)]  
  
## <a name="importing-a-public-key"></a><span data-ttu-id="8de65-196">Import veřejného klíče</span><span class="sxs-lookup"><span data-stu-id="8de65-196">Importing a Public Key</span></span>  
 <span data-ttu-id="8de65-197">Tato úloha načte klíč jenom s veřejnými parametry, jak je vytvořil `Export Public Key` tlačítko, a nastaví ho jako název kontejneru klíčů.</span><span class="sxs-lookup"><span data-stu-id="8de65-197">This task loads the key with only public parameters, as created by the `Export Public Key` button, and sets it as the key container name.</span></span>  
  
 <span data-ttu-id="8de65-198">Tato úloha simuluje scénář, který Bob načítá klíč Alice, jenom s veřejnými parametry, aby k nim mohl šifrovat soubory.</span><span class="sxs-lookup"><span data-stu-id="8de65-198">This task simulates the scenario of Bob loading Alice's key with only public parameters so he can encrypt files for her.</span></span>  
  
 <span data-ttu-id="8de65-199">Přidejte následující kód jako `Click` obslužnou rutinu události pro `Import Public Key` tlačítko ( `buttonImportPublicKey_Click` ).</span><span class="sxs-lookup"><span data-stu-id="8de65-199">Add the following code as the `Click` event handler for the `Import Public Key` button (`buttonImportPublicKey_Click`).</span></span>  
  
 [!code-csharp[CryptoWalkThru#9](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#9)]
 [!code-vb[CryptoWalkThru#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#9)]  
  
## <a name="getting-a-private-key"></a><span data-ttu-id="8de65-200">Získání privátního klíče</span><span class="sxs-lookup"><span data-stu-id="8de65-200">Getting a Private Key</span></span>  
 <span data-ttu-id="8de65-201">Tato úloha nastaví název kontejneru klíčů na název klíče vytvořeného pomocí `Create Keys` tlačítka.</span><span class="sxs-lookup"><span data-stu-id="8de65-201">This task sets the key container name to the name of the key created by using the `Create Keys` button.</span></span> <span data-ttu-id="8de65-202">Kontejner klíčů bude obsahovat úplný pár klíčů s privátními parametry.</span><span class="sxs-lookup"><span data-stu-id="8de65-202">The key container will contain the full key pair with private parameters.</span></span>  
  
 <span data-ttu-id="8de65-203">Tato úloha simuluje scénář Alice, který používá svůj privátní klíč k dešifrování souborů šifrovaných Bobem.</span><span class="sxs-lookup"><span data-stu-id="8de65-203">This task simulates the scenario of Alice using her private key to decrypt files encrypted by Bob.</span></span>  
  
 <span data-ttu-id="8de65-204">Přidejte následující kód jako `Click` obslužnou rutinu události pro `Get Private Key` tlačítko ( `buttonGetPrivateKey_Click` ).</span><span class="sxs-lookup"><span data-stu-id="8de65-204">Add the following code as the `Click` event handler for the `Get Private Key` button (`buttonGetPrivateKey_Click`).</span></span>  
  
 [!code-csharp[CryptoWalkThru#7](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#7)]
 [!code-vb[CryptoWalkThru#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#7)]  
  
## <a name="testing-the-application"></a><span data-ttu-id="8de65-205">Testování aplikace</span><span class="sxs-lookup"><span data-stu-id="8de65-205">Testing the Application</span></span>  
 <span data-ttu-id="8de65-206">Po vytvoření aplikace proveďte následující testovací scénáře.</span><span class="sxs-lookup"><span data-stu-id="8de65-206">After you have built the application, perform the following testing scenarios.</span></span>  
  
#### <a name="to-create-keys-encrypt-and-decrypt"></a><span data-ttu-id="8de65-207">Vytvoření klíčů, šifrování a dešifrování</span><span class="sxs-lookup"><span data-stu-id="8de65-207">To create keys, encrypt, and decrypt</span></span>  
  
1. <span data-ttu-id="8de65-208">Klikněte na tlačítko `Create Keys`.</span><span class="sxs-lookup"><span data-stu-id="8de65-208">Click the `Create Keys` button.</span></span> <span data-ttu-id="8de65-209">Popisek zobrazí název klíče a ukáže, že se jedná o úplný pár klíčů.</span><span class="sxs-lookup"><span data-stu-id="8de65-209">The label displays the key name and shows that it is a full key pair.</span></span>  
  
2. <span data-ttu-id="8de65-210">Klikněte na tlačítko `Export Public Key`.</span><span class="sxs-lookup"><span data-stu-id="8de65-210">Click the `Export Public Key` button.</span></span> <span data-ttu-id="8de65-211">Všimněte si, že export parametrů veřejného klíče nemění aktuální klíč.</span><span class="sxs-lookup"><span data-stu-id="8de65-211">Note that exporting the public key parameters does not change the current key.</span></span>  
  
3. <span data-ttu-id="8de65-212">Klikněte na `Encrypt File` tlačítko a vyberte soubor.</span><span class="sxs-lookup"><span data-stu-id="8de65-212">Click the `Encrypt File` button and select a file.</span></span>  
  
4. <span data-ttu-id="8de65-213">Klikněte na `Decrypt File` tlačítko a vyberte soubor právě zašifrovaný.</span><span class="sxs-lookup"><span data-stu-id="8de65-213">Click the `Decrypt File` button and select the file just encrypted.</span></span>  
  
5. <span data-ttu-id="8de65-214">Prověřte soubor, který se právě dešifroval.</span><span class="sxs-lookup"><span data-stu-id="8de65-214">Examine the file just decrypted.</span></span>  
  
6. <span data-ttu-id="8de65-215">Zavřete aplikaci a restartujte ji, abyste v dalším scénáři otestovali načtení trvalých kontejnerů klíčů.</span><span class="sxs-lookup"><span data-stu-id="8de65-215">Close the application and restart it to test retrieving persisted key containers in the next scenario.</span></span>  
  
#### <a name="to-encrypt-using-the-public-key"></a><span data-ttu-id="8de65-216">Šifrování pomocí veřejného klíče</span><span class="sxs-lookup"><span data-stu-id="8de65-216">To encrypt using the public key</span></span>  
  
1. <span data-ttu-id="8de65-217">Klikněte na tlačítko `Import Public Key`.</span><span class="sxs-lookup"><span data-stu-id="8de65-217">Click the `Import Public Key` button.</span></span> <span data-ttu-id="8de65-218">Popisek zobrazí název klíče a ukáže, že je pouze veřejný.</span><span class="sxs-lookup"><span data-stu-id="8de65-218">The label displays the key name and shows that it is public only.</span></span>  
  
2. <span data-ttu-id="8de65-219">Klikněte na `Encrypt File` tlačítko a vyberte soubor.</span><span class="sxs-lookup"><span data-stu-id="8de65-219">Click the `Encrypt File` button and select a file.</span></span>  
  
3. <span data-ttu-id="8de65-220">Klikněte na `Decrypt File` tlačítko a vyberte soubor právě zašifrovaný.</span><span class="sxs-lookup"><span data-stu-id="8de65-220">Click the `Decrypt File` button and select the file just encrypted.</span></span> <span data-ttu-id="8de65-221">To se nezdaří, protože musíte mít privátní klíč k dešifrování.</span><span class="sxs-lookup"><span data-stu-id="8de65-221">This will fail because you must have the private key to decrypt.</span></span>  
  
 <span data-ttu-id="8de65-222">Tento scénář ukazuje pouze veřejný klíč k šifrování souboru pro jinou osobu.</span><span class="sxs-lookup"><span data-stu-id="8de65-222">This scenario demonstrates having only the public key to encrypt a file for another person.</span></span> <span data-ttu-id="8de65-223">Obvykle vám někdo poskytne jenom veřejný klíč a odpírá privátní klíč k dešifrování.</span><span class="sxs-lookup"><span data-stu-id="8de65-223">Typically that person would give you only the public key and withhold the private key for decryption.</span></span>  
  
#### <a name="to-decrypt-using-the-private-key"></a><span data-ttu-id="8de65-224">Dešifrování pomocí privátního klíče</span><span class="sxs-lookup"><span data-stu-id="8de65-224">To decrypt using the private key</span></span>  
  
1. <span data-ttu-id="8de65-225">Klikněte na tlačítko `Get Private Key`.</span><span class="sxs-lookup"><span data-stu-id="8de65-225">Click the `Get Private Key` button.</span></span> <span data-ttu-id="8de65-226">Popisek zobrazí název klíče a ukáže, zda se jedná o úplný pár klíčů.</span><span class="sxs-lookup"><span data-stu-id="8de65-226">The label displays the key name and shows whether it is the full key pair.</span></span>  
  
2. <span data-ttu-id="8de65-227">Klikněte na `Decrypt File` tlačítko a vyberte soubor právě zašifrovaný.</span><span class="sxs-lookup"><span data-stu-id="8de65-227">Click the `Decrypt File` button and select the file just encrypted.</span></span> <span data-ttu-id="8de65-228">Tato akce bude úspěšná, protože máte úplný pár klíčů k dešifrování.</span><span class="sxs-lookup"><span data-stu-id="8de65-228">This will be successful because you have the full key pair to decrypt.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8de65-229">Viz také</span><span class="sxs-lookup"><span data-stu-id="8de65-229">See also</span></span>

- [<span data-ttu-id="8de65-230">Kryptografické služby</span><span class="sxs-lookup"><span data-stu-id="8de65-230">Cryptographic Services</span></span>](cryptographic-services.md)
