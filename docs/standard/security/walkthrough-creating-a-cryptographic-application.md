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
ms.openlocfilehash: 77debed932b78ae0aa1d8eebf54bd2d3bfbfea7a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33591960"
---
# <a name="walkthrough-creating-a-cryptographic-application"></a><span data-ttu-id="fb2bf-102">Návod: Vytvoření šifrovací aplikace</span><span class="sxs-lookup"><span data-stu-id="fb2bf-102">Walkthrough: Creating a Cryptographic Application</span></span>
<span data-ttu-id="fb2bf-103">Tento návod ukazuje, jak k šifrování a dešifrování obsahu.</span><span class="sxs-lookup"><span data-stu-id="fb2bf-103">This walkthrough demonstrates how to encrypt and decrypt content.</span></span> <span data-ttu-id="fb2bf-104">Ukázky kódu jsou navrženy pro aplikace Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="fb2bf-104">The code examples are designed for a Windows Forms application.</span></span> <span data-ttu-id="fb2bf-105">Tuto aplikaci nepředvádí skutečných scénářích, například pomocí čipové karty.</span><span class="sxs-lookup"><span data-stu-id="fb2bf-105">This application does not demonstrate real world scenarios, such as using smart cards.</span></span> <span data-ttu-id="fb2bf-106">Místo toho ukazuje základní informace o šifrování a dešifrování.</span><span class="sxs-lookup"><span data-stu-id="fb2bf-106">Instead, it demonstrates the fundamentals of encryption and decryption.</span></span>  
  
 <span data-ttu-id="fb2bf-107">Tento návod používá pro šifrování následující pokyny:</span><span class="sxs-lookup"><span data-stu-id="fb2bf-107">This walkthrough uses the following guidelines for encryption:</span></span>  
  
-   <span data-ttu-id="fb2bf-108">Použití <xref:System.Security.Cryptography.RijndaelManaged> třídy symetrický algoritmus, k šifrování a dešifrování dat pomocí jeho automaticky generované <xref:System.Security.Cryptography.SymmetricAlgorithm.Key%2A> a <xref:System.Security.Cryptography.SymmetricAlgorithm.IV%2A>.</span><span class="sxs-lookup"><span data-stu-id="fb2bf-108">Use the <xref:System.Security.Cryptography.RijndaelManaged> class, a symmetric algorithm, to encrypt and decrypt data by using its automatically generated <xref:System.Security.Cryptography.SymmetricAlgorithm.Key%2A> and <xref:System.Security.Cryptography.SymmetricAlgorithm.IV%2A>.</span></span>  
  
-   <span data-ttu-id="fb2bf-109">Použití <xref:System.Security.Cryptography.RSACryptoServiceProvider>, asymetrického algoritmu, k šifrování a dešifrování klíče, který se data zašifrovaná pomocí <xref:System.Security.Cryptography.RijndaelManaged>.</span><span class="sxs-lookup"><span data-stu-id="fb2bf-109">Use the <xref:System.Security.Cryptography.RSACryptoServiceProvider>, an asymmetric algorithm, to encrypt and decrypt the key to the data encrypted by <xref:System.Security.Cryptography.RijndaelManaged>.</span></span> <span data-ttu-id="fb2bf-110">Asymetrické algoritmy jsou nejvhodnější pro menší množství dat, jako jsou klíče.</span><span class="sxs-lookup"><span data-stu-id="fb2bf-110">Asymmetric algorithms are best used for smaller amounts of data, such as a key.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="fb2bf-111">Pokud chcete chránit data ve vašem počítači místo výměny šifrovaný obsah s jinými uživateli, zvažte použití <xref:System.Security.Cryptography.ProtectedData> nebo <xref:System.Security.Cryptography.ProtectedMemory> třídy.</span><span class="sxs-lookup"><span data-stu-id="fb2bf-111">If you want to protect data on your computer instead of exchanging encrypted content with other people, consider using the <xref:System.Security.Cryptography.ProtectedData> or <xref:System.Security.Cryptography.ProtectedMemory> classes.</span></span>  
  
 <span data-ttu-id="fb2bf-112">Následující tabulka shrnuje kryptografické úlohy v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="fb2bf-112">The following table summarizes the cryptographic tasks in this topic.</span></span>  
  
|<span data-ttu-id="fb2bf-113">Úloha</span><span class="sxs-lookup"><span data-stu-id="fb2bf-113">Task</span></span>|<span data-ttu-id="fb2bf-114">Popis</span><span class="sxs-lookup"><span data-stu-id="fb2bf-114">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="fb2bf-115">Vytvoření aplikace pro Windows Forms</span><span class="sxs-lookup"><span data-stu-id="fb2bf-115">Creating a Windows Forms application</span></span>|<span data-ttu-id="fb2bf-116">Uvádí ovládacích prvků, které jsou nutné ke spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="fb2bf-116">Lists the controls that are required to run the application.</span></span>|  
|<span data-ttu-id="fb2bf-117">Deklarování globální objekty</span><span class="sxs-lookup"><span data-stu-id="fb2bf-117">Declaring global objects</span></span>|<span data-ttu-id="fb2bf-118">Deklaruje řetězec proměnné cest, <xref:System.Security.Cryptography.CspParameters>a <xref:System.Security.Cryptography.RSACryptoServiceProvider> tak, aby měl globální kontextu <xref:System.Windows.Forms.Form> třídy.</span><span class="sxs-lookup"><span data-stu-id="fb2bf-118">Declares string path variables, the <xref:System.Security.Cryptography.CspParameters>, and the <xref:System.Security.Cryptography.RSACryptoServiceProvider> to have global context of the <xref:System.Windows.Forms.Form> class.</span></span>|  
|<span data-ttu-id="fb2bf-119">Vytváření asymetrického klíče</span><span class="sxs-lookup"><span data-stu-id="fb2bf-119">Creating an asymmetric key</span></span>|<span data-ttu-id="fb2bf-120">Vytvoří dvojici asymetrické veřejné a soukromé klíče hodnotu a přiřadí ji název kontejneru klíčů.</span><span class="sxs-lookup"><span data-stu-id="fb2bf-120">Creates an asymmetric public and private key value pair and assigns it a key container name.</span></span>|  
|<span data-ttu-id="fb2bf-121">Šifrování souboru</span><span class="sxs-lookup"><span data-stu-id="fb2bf-121">Encrypting a file</span></span>|<span data-ttu-id="fb2bf-122">Zobrazí dialogové okno a vyberte soubor pro šifrování a zašifrování souboru.</span><span class="sxs-lookup"><span data-stu-id="fb2bf-122">Displays a dialog box to select a file for encryption and encrypts the file.</span></span>|  
|<span data-ttu-id="fb2bf-123">Dešifrování souboru</span><span class="sxs-lookup"><span data-stu-id="fb2bf-123">Decrypting a file</span></span>|<span data-ttu-id="fb2bf-124">Zobrazí dialogové okno vybrat zašifrovaný soubor pro dešifrování a soubor dešifruje.</span><span class="sxs-lookup"><span data-stu-id="fb2bf-124">Displays a dialog box to select an encrypted file for decryption and decrypts the file.</span></span>|  
|<span data-ttu-id="fb2bf-125">Získání privátního klíče</span><span class="sxs-lookup"><span data-stu-id="fb2bf-125">Getting a private key</span></span>|<span data-ttu-id="fb2bf-126">Získá úplný pár klíče pomocí názvu kontejneru klíčů.</span><span class="sxs-lookup"><span data-stu-id="fb2bf-126">Gets the full key pair using the key container name.</span></span>|  
|<span data-ttu-id="fb2bf-127">Export veřejného klíče</span><span class="sxs-lookup"><span data-stu-id="fb2bf-127">Exporting a public key</span></span>|<span data-ttu-id="fb2bf-128">Uloží klíč do souboru XML s pouze veřejné parametry.</span><span class="sxs-lookup"><span data-stu-id="fb2bf-128">Saves the key to an XML file with only public parameters.</span></span>|  
|<span data-ttu-id="fb2bf-129">Import veřejného klíče</span><span class="sxs-lookup"><span data-stu-id="fb2bf-129">Importing a public key</span></span>|<span data-ttu-id="fb2bf-130">Načte klíče ze souboru XML do kontejneru klíčů.</span><span class="sxs-lookup"><span data-stu-id="fb2bf-130">Loads the key from an XML file into the key container.</span></span>|  
|<span data-ttu-id="fb2bf-131">Testování aplikace</span><span class="sxs-lookup"><span data-stu-id="fb2bf-131">Testing the application</span></span>|<span data-ttu-id="fb2bf-132">Uvádí postupy pro testování této aplikace.</span><span class="sxs-lookup"><span data-stu-id="fb2bf-132">Lists procedures for testing this application.</span></span>|  
  
## <a name="prerequisites"></a><span data-ttu-id="fb2bf-133">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fb2bf-133">Prerequisites</span></span>  
 <span data-ttu-id="fb2bf-134">K dokončení tohoto návodu budete potřebovat následující komponenty:</span><span class="sxs-lookup"><span data-stu-id="fb2bf-134">You need the following components to complete this walkthrough:</span></span>  
  
-   <span data-ttu-id="fb2bf-135">Odkazuje na <xref:System.IO> a <xref:System.Security.Cryptography> obory názvů.</span><span class="sxs-lookup"><span data-stu-id="fb2bf-135">References to the <xref:System.IO> and <xref:System.Security.Cryptography> namespaces.</span></span>  
  
## <a name="creating-a-windows-forms-application"></a><span data-ttu-id="fb2bf-136">Vytvoření aplikace Windows Forms</span><span class="sxs-lookup"><span data-stu-id="fb2bf-136">Creating a Windows Forms Application</span></span>  
 <span data-ttu-id="fb2bf-137">Většina příklady kódu v tomto průvodci jsou navržené jako obslužné rutiny události pro ovládací prvky tlačítek.</span><span class="sxs-lookup"><span data-stu-id="fb2bf-137">Most of the code examples in this walkthrough are designed to be event handlers for button controls.</span></span> <span data-ttu-id="fb2bf-138">Následující tabulka uvádí prvky, které jsou vyžadovány pro ukázkovou aplikaci a jejich požadované názvy tak, aby odpovídaly příklady kódu.</span><span class="sxs-lookup"><span data-stu-id="fb2bf-138">The following table lists the controls required for the sample application and their required names to match the code examples.</span></span>  
  
|<span data-ttu-id="fb2bf-139">Ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="fb2bf-139">Control</span></span>|<span data-ttu-id="fb2bf-140">Název</span><span class="sxs-lookup"><span data-stu-id="fb2bf-140">Name</span></span>|<span data-ttu-id="fb2bf-141">Text – vlastnost (podle potřeby)</span><span class="sxs-lookup"><span data-stu-id="fb2bf-141">Text property (as needed)</span></span>|  
|-------------|----------|---------------------------------|  
|<xref:System.Windows.Forms.Button>|`buttonEncryptFile`|<span data-ttu-id="fb2bf-142">Šifrování souborů</span><span class="sxs-lookup"><span data-stu-id="fb2bf-142">Encrypt File</span></span>|  
|<xref:System.Windows.Forms.Button>|`buttonDecryptFile`|<span data-ttu-id="fb2bf-143">Dešifrování souboru</span><span class="sxs-lookup"><span data-stu-id="fb2bf-143">Decrypt File</span></span>|  
|<xref:System.Windows.Forms.Button>|`buttonCreateAsmKeys`|<span data-ttu-id="fb2bf-144">Vytvoření klíčů</span><span class="sxs-lookup"><span data-stu-id="fb2bf-144">Create Keys</span></span>|  
|<xref:System.Windows.Forms.Button>|`buttonExportPublicKey`|<span data-ttu-id="fb2bf-145">Export veřejného klíče</span><span class="sxs-lookup"><span data-stu-id="fb2bf-145">Export Public Key</span></span>|  
|<xref:System.Windows.Forms.Button>|`buttonImportPublicKey`|<span data-ttu-id="fb2bf-146">Import veřejného klíče</span><span class="sxs-lookup"><span data-stu-id="fb2bf-146">Import Public Key</span></span>|  
|<xref:System.Windows.Forms.Button>|`buttonGetPrivateKey`|<span data-ttu-id="fb2bf-147">Získání privátního klíče</span><span class="sxs-lookup"><span data-stu-id="fb2bf-147">Get Private Key</span></span>|  
|<xref:System.Windows.Forms.Label>|`label1`||  
|<xref:System.Windows.Forms.OpenFileDialog>|`openFileDialog1`||  
|<xref:System.Windows.Forms.OpenFileDialog>|`openFileDialog2`||  
  
 <span data-ttu-id="fb2bf-148">Dvakrát klikněte na tlačítka v návrháři Visual Studio k vytvoření jejich obslužných rutin událostí.</span><span class="sxs-lookup"><span data-stu-id="fb2bf-148">Double-click the buttons in the  Visual Studio designer to create their event handlers.</span></span>  
  
## <a name="declaring-global-objects"></a><span data-ttu-id="fb2bf-149">Deklarování globální objekty</span><span class="sxs-lookup"><span data-stu-id="fb2bf-149">Declaring Global Objects</span></span>  
 <span data-ttu-id="fb2bf-150">Přidejte následující kód do konstruktoru formuláře.</span><span class="sxs-lookup"><span data-stu-id="fb2bf-150">Add the following code to the Form's constructor.</span></span> <span data-ttu-id="fb2bf-151">Upravte proměnné řetězce pro vaše prostředí a předvolbám.</span><span class="sxs-lookup"><span data-stu-id="fb2bf-151">Edit the string variables for your environment and preferences.</span></span>  
  
 [!code-csharp[CryptoWalkThru#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#1)]
 [!code-vb[CryptoWalkThru#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#1)]  
  
## <a name="creating-an-asymmetric-key"></a><span data-ttu-id="fb2bf-152">Vytváření asymetrického klíče</span><span class="sxs-lookup"><span data-stu-id="fb2bf-152">Creating an Asymmetric Key</span></span>  
 <span data-ttu-id="fb2bf-153">Tato úloha vytvoří asymetrický klíč, který šifruje a dešifruje <xref:System.Security.Cryptography.RijndaelManaged> klíč.</span><span class="sxs-lookup"><span data-stu-id="fb2bf-153">This task creates an asymmetric key that encrypts and decrypts the <xref:System.Security.Cryptography.RijndaelManaged> key.</span></span> <span data-ttu-id="fb2bf-154">Tento klíč se používá k šifrování obsahu a zobrazí se název kontejneru klíčů na ovládací prvek popisek.</span><span class="sxs-lookup"><span data-stu-id="fb2bf-154">This key was used to encrypt the content and it displays the key container name on the label control.</span></span>  
  
 <span data-ttu-id="fb2bf-155">Přidejte následující kód, jako `Click` obslužné rutiny události pro `Create Keys` tlačítko (`buttonCreateAsmKeys_Click`).</span><span class="sxs-lookup"><span data-stu-id="fb2bf-155">Add the following code as the `Click` event handler for the `Create Keys` button (`buttonCreateAsmKeys_Click`).</span></span>  
  
 [!code-csharp[CryptoWalkThru#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#2)]
 [!code-vb[CryptoWalkThru#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#2)]  
  
## <a name="encrypting-a-file"></a><span data-ttu-id="fb2bf-156">Šifrování souboru</span><span class="sxs-lookup"><span data-stu-id="fb2bf-156">Encrypting a File</span></span>  
 <span data-ttu-id="fb2bf-157">Tato úloha zahrnuje dvě metody: metodu obslužné rutiny události pro `Encrypt File` tlačítko (`buttonEncryptFile_Click`) a `EncryptFile` metoda.</span><span class="sxs-lookup"><span data-stu-id="fb2bf-157">This task involves two methods: the event handler method for the `Encrypt File` button (`buttonEncryptFile_Click`) and the `EncryptFile` method.</span></span> <span data-ttu-id="fb2bf-158">První metoda zobrazí dialogové okno pro výběr souboru a předá název souboru do druhé metody, které provádí šifrování.</span><span class="sxs-lookup"><span data-stu-id="fb2bf-158">The first method displays a dialog box for selecting a file and passes the file name to the second method, which performs the encryption.</span></span>  
  
 <span data-ttu-id="fb2bf-159">Šifrovaný obsah, klíče a IV všechna uložena do jednoho <xref:System.IO.FileStream>, což se označuje jako balíčku šifrování.</span><span class="sxs-lookup"><span data-stu-id="fb2bf-159">The encrypted content, key, and IV are all saved to one <xref:System.IO.FileStream>, which is referred to as the encryption package.</span></span>  
  
 <span data-ttu-id="fb2bf-160">`EncryptFile` Metoda provede následující akce:</span><span class="sxs-lookup"><span data-stu-id="fb2bf-160">The `EncryptFile` method does the following:</span></span>  
  
1.  <span data-ttu-id="fb2bf-161">Vytvoří <xref:System.Security.Cryptography.RijndaelManaged> algoritmus symetrického šifrování obsahu.</span><span class="sxs-lookup"><span data-stu-id="fb2bf-161">Creates a <xref:System.Security.Cryptography.RijndaelManaged> symmetric algorithm to encrypt the content.</span></span>  
  
2.  <span data-ttu-id="fb2bf-162">Vytvoří <xref:System.Security.Cryptography.RSACryptoServiceProvider> objekt, který chcete zašifrovat <xref:System.Security.Cryptography.RijndaelManaged> klíč.</span><span class="sxs-lookup"><span data-stu-id="fb2bf-162">Creates an <xref:System.Security.Cryptography.RSACryptoServiceProvider> object to encrypt the <xref:System.Security.Cryptography.RijndaelManaged> key.</span></span>  
  
3.  <span data-ttu-id="fb2bf-163">Používá <xref:System.Security.Cryptography.CryptoStream> objekt ke čtení a šifrování <xref:System.IO.FileStream> zdrojového souboru v blocích bajtů do cílového <xref:System.IO.FileStream> objekt pro šifrovaný soubor.</span><span class="sxs-lookup"><span data-stu-id="fb2bf-163">Uses a <xref:System.Security.Cryptography.CryptoStream> object to read and encrypt the <xref:System.IO.FileStream> of the source file, in blocks of bytes, into a destination <xref:System.IO.FileStream> object for the encrypted file.</span></span>  
  
4.  <span data-ttu-id="fb2bf-164">Určuje délky zašifrovaný klíč a IV a vytvoří jejich hodnoty pro délku pole bajtů.</span><span class="sxs-lookup"><span data-stu-id="fb2bf-164">Determines the lengths of the encrypted key and IV, and creates byte arrays of their length values.</span></span>  
  
5.  <span data-ttu-id="fb2bf-165">Zapíše klíč, IV a jejich hodnoty pro délku do šifrovaného balíčku.</span><span class="sxs-lookup"><span data-stu-id="fb2bf-165">Writes the Key, IV, and their length values to the encrypted package.</span></span>  
  
 <span data-ttu-id="fb2bf-166">Balíček šifrování používá následující formát:</span><span class="sxs-lookup"><span data-stu-id="fb2bf-166">The encryption package uses the following format:</span></span>  
  
-   <span data-ttu-id="fb2bf-167">Délka klíče, bajtů 0 - 3</span><span class="sxs-lookup"><span data-stu-id="fb2bf-167">Key length, bytes 0 - 3</span></span>  
  
-   <span data-ttu-id="fb2bf-168">Délka IV, bajty 4-7</span><span class="sxs-lookup"><span data-stu-id="fb2bf-168">IV length, bytes 4 - 7</span></span>  
  
-   <span data-ttu-id="fb2bf-169">Šifrovaný klíč</span><span class="sxs-lookup"><span data-stu-id="fb2bf-169">Encrypted key</span></span>  
  
-   <span data-ttu-id="fb2bf-170">IV</span><span class="sxs-lookup"><span data-stu-id="fb2bf-170">IV</span></span>  
  
-   <span data-ttu-id="fb2bf-171">Šifrovaný text</span><span class="sxs-lookup"><span data-stu-id="fb2bf-171">Cipher text</span></span>  
  
 <span data-ttu-id="fb2bf-172">Délky klíče a IV můžete použít k určení počátečních bodů a délek všech částí šifrování balíčku, který můžete použít pro dešifrování souboru.</span><span class="sxs-lookup"><span data-stu-id="fb2bf-172">You can use the lengths of the key and IV to determine the starting points and lengths of all parts of the encryption package, which can then be used to decrypt the file.</span></span>  
  
 <span data-ttu-id="fb2bf-173">Přidejte následující kód, jako `Click` obslužné rutiny události pro `Encrypt File` tlačítko (`buttonEncryptFile_Click`).</span><span class="sxs-lookup"><span data-stu-id="fb2bf-173">Add the following code as the `Click` event handler for the `Encrypt File` button (`buttonEncryptFile_Click`).</span></span>  
  
 [!code-csharp[CryptoWalkThru#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#3)]
 [!code-vb[CryptoWalkThru#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#3)]  
  
 <span data-ttu-id="fb2bf-174">Přidejte následující `EncryptFile` metoda do formuláře.</span><span class="sxs-lookup"><span data-stu-id="fb2bf-174">Add the following `EncryptFile` method to the form.</span></span>  
  
 [!code-csharp[CryptoWalkThru#5](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#5)]
 [!code-vb[CryptoWalkThru#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#5)]  
  
## <a name="decrypting-a-file"></a><span data-ttu-id="fb2bf-175">Dešifrování souboru</span><span class="sxs-lookup"><span data-stu-id="fb2bf-175">Decrypting a File</span></span>  
 <span data-ttu-id="fb2bf-176">Tato úloha zahrnuje dvě metody, metodu obslužné rutiny události pro `Decrypt File` tlačítko (`buttonEncryptFile_Click`) a `DecryptFile` metoda.</span><span class="sxs-lookup"><span data-stu-id="fb2bf-176">This task involves two methods, the event handler method for the `Decrypt File` button (`buttonEncryptFile_Click`), and the `DecryptFile` method.</span></span> <span data-ttu-id="fb2bf-177">První metoda zobrazí dialogové okno pro výběr souboru a předá její název souboru do druhé metody, která provádí dešifrování.</span><span class="sxs-lookup"><span data-stu-id="fb2bf-177">The first method displays a dialog box for selecting a file and passes its file name to the second method, which performs the decryption.</span></span>  
  
 <span data-ttu-id="fb2bf-178">`Decrypt` Metoda provede následující akce:</span><span class="sxs-lookup"><span data-stu-id="fb2bf-178">The `Decrypt` method does the following:</span></span>  
  
1.  <span data-ttu-id="fb2bf-179">Vytvoří <xref:System.Security.Cryptography.RijndaelManaged> symetrický algoritmus k dešifrování obsahu.</span><span class="sxs-lookup"><span data-stu-id="fb2bf-179">Creates a <xref:System.Security.Cryptography.RijndaelManaged> symmetric algorithm to decrypt the content.</span></span>  
  
2.  <span data-ttu-id="fb2bf-180">Přečte první osm bajtů <xref:System.IO.FileStream> šifrovaného balíčku do pole bajtů k získání délky zašifrovaný klíč a IV.</span><span class="sxs-lookup"><span data-stu-id="fb2bf-180">Reads the first eight bytes of the <xref:System.IO.FileStream> of the encrypted package into byte arrays to obtain the lengths of the encrypted key and the IV.</span></span>  
  
3.  <span data-ttu-id="fb2bf-181">Extrahuje klíče a IV z balíčku šifrování do pole bajtů.</span><span class="sxs-lookup"><span data-stu-id="fb2bf-181">Extracts the key and IV from the encryption package into byte arrays.</span></span>  
  
4.  <span data-ttu-id="fb2bf-182">Vytvoří <xref:System.Security.Cryptography.RSACryptoServiceProvider> objektu k dešifrování <xref:System.Security.Cryptography.RijndaelManaged> klíč.</span><span class="sxs-lookup"><span data-stu-id="fb2bf-182">Creates an <xref:System.Security.Cryptography.RSACryptoServiceProvider> object to decrypt the <xref:System.Security.Cryptography.RijndaelManaged> key.</span></span>  
  
5.  <span data-ttu-id="fb2bf-183">Používá <xref:System.Security.Cryptography.CryptoStream> objekt ke čtení a dešifrování části textu šifrovací <xref:System.IO.FileStream> šifrování balíčku, v blocích bajtů do <xref:System.IO.FileStream> objekt pro dešifrovaný soubor.</span><span class="sxs-lookup"><span data-stu-id="fb2bf-183">Uses a <xref:System.Security.Cryptography.CryptoStream> object to read and decrypt the cipher text section of the <xref:System.IO.FileStream> encryption package, in blocks of bytes, into the <xref:System.IO.FileStream> object for the decrypted file.</span></span> <span data-ttu-id="fb2bf-184">Po jejím dokončení, dešifrování je dokončeno.</span><span class="sxs-lookup"><span data-stu-id="fb2bf-184">When this is finished, the decryption is completed.</span></span>  
  
 <span data-ttu-id="fb2bf-185">Přidejte následující kód, jako `Click` obslužné rutiny události pro `Decrypt File` tlačítko.</span><span class="sxs-lookup"><span data-stu-id="fb2bf-185">Add the following code as the `Click` event handler for the `Decrypt File` button.</span></span>  
  
 [!code-csharp[CryptoWalkThru#4](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#4)]
 [!code-vb[CryptoWalkThru#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#4)]  
  
 <span data-ttu-id="fb2bf-186">Přidejte následující `DecryptFile` metoda do formuláře.</span><span class="sxs-lookup"><span data-stu-id="fb2bf-186">Add the following `DecryptFile` method to the form.</span></span>  
  
 [!code-csharp[CryptoWalkThru#6](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#6)]
 [!code-vb[CryptoWalkThru#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#6)]  
  
## <a name="exporting-a-public-key"></a><span data-ttu-id="fb2bf-187">Export veřejného klíče</span><span class="sxs-lookup"><span data-stu-id="fb2bf-187">Exporting a Public Key</span></span>  
 <span data-ttu-id="fb2bf-188">Tato úloha uloží klíč vytvořený `Create Keys` tlačítko do souboru.</span><span class="sxs-lookup"><span data-stu-id="fb2bf-188">This task saves the key created by the `Create Keys` button to a file.</span></span> <span data-ttu-id="fb2bf-189">Exportuje pouze veřejné parametry.</span><span class="sxs-lookup"><span data-stu-id="fb2bf-189">It exports only the public parameters.</span></span>  
  
 <span data-ttu-id="fb2bf-190">Tato úloha simuluje scénář Alice poskytnutí Bob svůj veřejný klíč, aby mohl šifrovat soubory pro ní.</span><span class="sxs-lookup"><span data-stu-id="fb2bf-190">This task simulates the scenario of Alice giving Bob her public key so that he can encrypt files for her.</span></span> <span data-ttu-id="fb2bf-191">On a ostatní používající tento veřejný klíč, nebudou moci dešifrovat, protože nemají úplný pár klíče s privátní parametry.</span><span class="sxs-lookup"><span data-stu-id="fb2bf-191">He and others who have that public key will not be able to decrypt them because they do not have the full key pair with private parameters.</span></span>  
  
 <span data-ttu-id="fb2bf-192">Přidejte následující kód, jako `Click` obslužné rutiny události pro `Export Public Key` tlačítko (`buttonExportPublicKey_Click`).</span><span class="sxs-lookup"><span data-stu-id="fb2bf-192">Add the following code as the `Click` event handler for the `Export Public Key` button (`buttonExportPublicKey_Click`).</span></span>  
  
 [!code-csharp[CryptoWalkThru#8](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#8)]
 [!code-vb[CryptoWalkThru#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#8)]  
  
## <a name="importing-a-public-key"></a><span data-ttu-id="fb2bf-193">Import veřejného klíče</span><span class="sxs-lookup"><span data-stu-id="fb2bf-193">Importing a Public Key</span></span>  
 <span data-ttu-id="fb2bf-194">Tato úloha načte klíč s pouze veřejné parametry, jak je vytvořený `Export Public Key` tlačítko a nastaví jej jako název kontejneru klíče.</span><span class="sxs-lookup"><span data-stu-id="fb2bf-194">This task loads the key with only public parameters, as created by the `Export Public Key` button, and sets it as the key container name.</span></span>  
  
 <span data-ttu-id="fb2bf-195">Tato úloha simuluje scénář Bob načítání klíče Alice s pouze veřejné parametry, tak pro ní může šifrovat soubory.</span><span class="sxs-lookup"><span data-stu-id="fb2bf-195">This task simulates the scenario of Bob loading Alice's key with only public parameters so he can encrypt files for her.</span></span>  
  
 <span data-ttu-id="fb2bf-196">Přidejte následující kód, jako `Click` obslužné rutiny události pro `Import Public Key` tlačítko (`buttonImportPublicKey_Click`).</span><span class="sxs-lookup"><span data-stu-id="fb2bf-196">Add the following code as the `Click` event handler for the `Import Public Key` button (`buttonImportPublicKey_Click`).</span></span>  
  
 [!code-csharp[CryptoWalkThru#9](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#9)]
 [!code-vb[CryptoWalkThru#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#9)]  
  
## <a name="getting-a-private-key"></a><span data-ttu-id="fb2bf-197">Získávání privátní klíč</span><span class="sxs-lookup"><span data-stu-id="fb2bf-197">Getting a Private Key</span></span>  
 <span data-ttu-id="fb2bf-198">Tato úloha nastaví název kontejneru klíče k názvu klíče vytvořeného pomocí `Create Keys` tlačítko.</span><span class="sxs-lookup"><span data-stu-id="fb2bf-198">This task sets the key container name to the name of the key created by using the `Create Keys` button.</span></span> <span data-ttu-id="fb2bf-199">Kontejner klíče bude obsahovat úplný pár klíče s privátní parametry.</span><span class="sxs-lookup"><span data-stu-id="fb2bf-199">The key container will contain the full key pair with private parameters.</span></span>  
  
 <span data-ttu-id="fb2bf-200">Tato úloha simuluje scénář, jak pomocí vlastního soukromého klíče k dešifrování souborů zašifrované Bob Alice.</span><span class="sxs-lookup"><span data-stu-id="fb2bf-200">This task simulates the scenario of Alice using her private key to decrypt files encrypted by Bob.</span></span>  
  
 <span data-ttu-id="fb2bf-201">Přidejte následující kód, jako `Click` obslužné rutiny události pro `Get Private Key` tlačítko (`buttonGetPrivateKey_Click`).</span><span class="sxs-lookup"><span data-stu-id="fb2bf-201">Add the following code as the `Click` event handler for the `Get Private Key` button (`buttonGetPrivateKey_Click`).</span></span>  
  
 [!code-csharp[CryptoWalkThru#7](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#7)]
 [!code-vb[CryptoWalkThru#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#7)]  
  
## <a name="testing-the-application"></a><span data-ttu-id="fb2bf-202">Testování aplikace</span><span class="sxs-lookup"><span data-stu-id="fb2bf-202">Testing the Application</span></span>  
 <span data-ttu-id="fb2bf-203">Po vytvoření aplikace, proveďte následující scénáře testování.</span><span class="sxs-lookup"><span data-stu-id="fb2bf-203">After you have built the application, perform the following testing scenarios.</span></span>  
  
#### <a name="to-create-keys-encrypt-and-decrypt"></a><span data-ttu-id="fb2bf-204">K vytvoření klíčů, šifrování a dešifrování</span><span class="sxs-lookup"><span data-stu-id="fb2bf-204">To create keys, encrypt, and decrypt</span></span>  
  
1.  <span data-ttu-id="fb2bf-205">Klikněte `Create Keys` tlačítko.</span><span class="sxs-lookup"><span data-stu-id="fb2bf-205">Click the `Create Keys` button.</span></span> <span data-ttu-id="fb2bf-206">Popisek zobrazí název klíče a ukazuje, že je to úplný pár klíče.</span><span class="sxs-lookup"><span data-stu-id="fb2bf-206">The label displays the key name and shows that it is a full key pair.</span></span>  
  
2.  <span data-ttu-id="fb2bf-207">Klikněte `Export Public Key` tlačítko.</span><span class="sxs-lookup"><span data-stu-id="fb2bf-207">Click the `Export Public Key` button.</span></span> <span data-ttu-id="fb2bf-208">Všimněte si, že export parametrů veřejného klíče nezmění aktuální klíč.</span><span class="sxs-lookup"><span data-stu-id="fb2bf-208">Note that exporting the public key parameters does not change the current key.</span></span>  
  
3.  <span data-ttu-id="fb2bf-209">Klikněte `Encrypt File` tlačítko a vyberte soubor.</span><span class="sxs-lookup"><span data-stu-id="fb2bf-209">Click the `Encrypt File` button and select a file.</span></span>  
  
4.  <span data-ttu-id="fb2bf-210">Klikněte `Decrypt File` tlačítko a vyberte soubor právě zašifrovaný.</span><span class="sxs-lookup"><span data-stu-id="fb2bf-210">Click the `Decrypt File` button and select the file just encrypted.</span></span>  
  
5.  <span data-ttu-id="fb2bf-211">Zkontrolujte v souboru právě dešifrovat.</span><span class="sxs-lookup"><span data-stu-id="fb2bf-211">Examine the file just decrypted.</span></span>  
  
6.  <span data-ttu-id="fb2bf-212">Zavřete aplikaci a restartujte ji k otestování načítání trvalých kontejnerů klíčů v dalším scénáři.</span><span class="sxs-lookup"><span data-stu-id="fb2bf-212">Close the application and restart it to test retrieving persisted key containers in the next scenario.</span></span>  
  
#### <a name="to-encrypt-using-the-public-key"></a><span data-ttu-id="fb2bf-213">K šifrování pomocí veřejného klíče</span><span class="sxs-lookup"><span data-stu-id="fb2bf-213">To encrypt using the public key</span></span>  
  
1.  <span data-ttu-id="fb2bf-214">Klikněte `Import Public Key` tlačítko.</span><span class="sxs-lookup"><span data-stu-id="fb2bf-214">Click the `Import Public Key` button.</span></span> <span data-ttu-id="fb2bf-215">Popisek zobrazí název klíče a ukazuje, že je veřejný pouze.</span><span class="sxs-lookup"><span data-stu-id="fb2bf-215">The label displays the key name and shows that it is public only.</span></span>  
  
2.  <span data-ttu-id="fb2bf-216">Klikněte `Encrypt File` tlačítko a vyberte soubor.</span><span class="sxs-lookup"><span data-stu-id="fb2bf-216">Click the `Encrypt File` button and select a file.</span></span>  
  
3.  <span data-ttu-id="fb2bf-217">Klikněte `Decrypt File` tlačítko a vyberte soubor právě zašifrovaný.</span><span class="sxs-lookup"><span data-stu-id="fb2bf-217">Click the `Decrypt File` button and select the file just encrypted.</span></span> <span data-ttu-id="fb2bf-218">To se nezdaří, protože musí mít privátní klíč pro dešifrování.</span><span class="sxs-lookup"><span data-stu-id="fb2bf-218">This will fail because you must have the private key to decrypt.</span></span>  
  
 <span data-ttu-id="fb2bf-219">Tento scénář ukazuje, jak máme pouze veřejný klíč k šifrování souboru pro jinou osobou.</span><span class="sxs-lookup"><span data-stu-id="fb2bf-219">This scenario demonstrates having only the public key to encrypt a file for another person.</span></span> <span data-ttu-id="fb2bf-220">Obvykle je tato osoba by získáte pouze veřejný klíč a odepřela soukromý klíč pro dešifrování.</span><span class="sxs-lookup"><span data-stu-id="fb2bf-220">Typically that person would give you only the public key and withhold the private key for decryption.</span></span>  
  
#### <a name="to-decrypt-using-the-private-key"></a><span data-ttu-id="fb2bf-221">Chcete-li dešifrovat pomocí soukromého klíče</span><span class="sxs-lookup"><span data-stu-id="fb2bf-221">To decrypt using the private key</span></span>  
  
1.  <span data-ttu-id="fb2bf-222">Klikněte `Get Private Key` tlačítko.</span><span class="sxs-lookup"><span data-stu-id="fb2bf-222">Click the `Get Private Key` button.</span></span> <span data-ttu-id="fb2bf-223">Popisek zobrazí název klíče a ukazuje, zda se jedná o úplný pár klíče.</span><span class="sxs-lookup"><span data-stu-id="fb2bf-223">The label displays the key name and shows whether it is the full key pair.</span></span>  
  
2.  <span data-ttu-id="fb2bf-224">Klikněte `Decrypt File` tlačítko a vyberte soubor právě zašifrovaný.</span><span class="sxs-lookup"><span data-stu-id="fb2bf-224">Click the `Decrypt File` button and select the file just encrypted.</span></span> <span data-ttu-id="fb2bf-225">Tato funkce bude úspěšné, protože máte úplný pár klíče k dešifrování.</span><span class="sxs-lookup"><span data-stu-id="fb2bf-225">This will be successful because you have the full key pair to decrypt.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb2bf-226">Viz také</span><span class="sxs-lookup"><span data-stu-id="fb2bf-226">See Also</span></span>  
 [<span data-ttu-id="fb2bf-227">Kryptografické služby</span><span class="sxs-lookup"><span data-stu-id="fb2bf-227">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)
