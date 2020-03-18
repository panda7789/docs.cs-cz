---
title: Jak vytvořit soubor nebo složku - C# Programovací průvodce
ms.date: 07/20/2015
helpviewer_keywords:
- folders [C#]
- creating files [C#]
- files [C#]
- creating folders [C#]
ms.assetid: 4582ee2d-d72d-4687-bcb9-08d336c62c25
ms.openlocfilehash: cdcc0a375aa1eca29c024d1e0c9008f337d0c772
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79167554"
---
# <a name="how-to-create-a-file-or-folder-c-programming-guide"></a><span data-ttu-id="9ecff-102">Jak vytvořit soubor nebo složku (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="9ecff-102">How to create a file or folder (C# Programming Guide)</span></span>
<span data-ttu-id="9ecff-103">Můžete programově vytvořit složku v počítači, vytvořit podsložku, vytvořit soubor v podsložce a zapsat data do souboru.</span><span class="sxs-lookup"><span data-stu-id="9ecff-103">You can programmatically create a folder on your computer, create a subfolder, create a file in the subfolder, and write data to the file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9ecff-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="9ecff-104">Example</span></span>  
 [!code-csharp[csFilesandFolders#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#10)]  
  
 <span data-ttu-id="9ecff-105">Pokud složka již existuje, <xref:System.IO.Directory.CreateDirectory%2A> neprovede žádnou akci a není vyvolána žádná výjimka.</span><span class="sxs-lookup"><span data-stu-id="9ecff-105">If the folder already exists, <xref:System.IO.Directory.CreateDirectory%2A> does nothing, and no exception is thrown.</span></span> <span data-ttu-id="9ecff-106">Nahradí <xref:System.IO.File.Create%2A?displayProperty=nameWithType> však existující soubor novým souborem.</span><span class="sxs-lookup"><span data-stu-id="9ecff-106">However, <xref:System.IO.File.Create%2A?displayProperty=nameWithType> replaces an existing file with a new file.</span></span> <span data-ttu-id="9ecff-107">Příklad používá `if` - `else` příkaz, který zabraňuje nahrazení existujícího souboru.</span><span class="sxs-lookup"><span data-stu-id="9ecff-107">The example uses an `if`-`else` statement to prevent an existing file from being replaced.</span></span>  
  
 <span data-ttu-id="9ecff-108">Provedením následujících změn v příkladu můžete určit různé výsledky na základě toho, zda soubor s určitým názvem již existuje.</span><span class="sxs-lookup"><span data-stu-id="9ecff-108">By making the following changes in the example, you can specify different outcomes based on whether a file with a certain name already exists.</span></span> <span data-ttu-id="9ecff-109">Pokud takový soubor neexistuje, kód jej vytvoří.</span><span class="sxs-lookup"><span data-stu-id="9ecff-109">If such a file doesn't exist, the code creates one.</span></span> <span data-ttu-id="9ecff-110">Pokud takový soubor existuje, kód připojí data k tomuto souboru.</span><span class="sxs-lookup"><span data-stu-id="9ecff-110">If such a file exists, the code appends data to that file.</span></span>  
  
- <span data-ttu-id="9ecff-111">Zadejte název nenáhodného souboru.</span><span class="sxs-lookup"><span data-stu-id="9ecff-111">Specify a non-random file name.</span></span>  
  
    ```csharp  
    // Comment out the following line.  
    //string fileName = System.IO.Path.GetRandomFileName();  
  
    // Replace that line with the following assignment.  
    string fileName = "MyNewFile.txt";  
    ```  
  
- <span data-ttu-id="9ecff-112">Nahraďte `if` - `else` příkaz `using` příkazem v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="9ecff-112">Replace the `if`-`else` statement with the `using` statement in the following code.</span></span>  
  
    ```csharp  
    using (System.IO.FileStream fs = new System.IO.FileStream(pathString, FileMode.Append))
    {  
        for (byte i = 0; i < 100; i++)  
        {  
            fs.WriteByte(i);  
        }  
    }  
    ```  
  
 <span data-ttu-id="9ecff-113">Spusťte příklad několikrát ověřit, že data jsou přidána do souboru pokaždé.</span><span class="sxs-lookup"><span data-stu-id="9ecff-113">Run the example several times to verify that data is added to the file each time.</span></span>  
  
 <span data-ttu-id="9ecff-114">Další `FileMode` hodnoty, které můžete <xref:System.IO.FileMode>vyzkoušet, naleznete v tématu .</span><span class="sxs-lookup"><span data-stu-id="9ecff-114">For more `FileMode` values that you can try, see <xref:System.IO.FileMode>.</span></span>  
  
 <span data-ttu-id="9ecff-115">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="9ecff-115">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="9ecff-116">Název složky je poškozen.</span><span class="sxs-lookup"><span data-stu-id="9ecff-116">The folder name is malformed.</span></span> <span data-ttu-id="9ecff-117">Obsahuje například neplatné znaky nebo je<xref:System.ArgumentException> pouze prázdné znaky (třída).</span><span class="sxs-lookup"><span data-stu-id="9ecff-117">For example, it contains illegal characters or is only white space (<xref:System.ArgumentException> class).</span></span> <span data-ttu-id="9ecff-118">Pomocí <xref:System.IO.Path> třídy vytvořte platné názvy cest.</span><span class="sxs-lookup"><span data-stu-id="9ecff-118">Use the <xref:System.IO.Path> class to create valid path names.</span></span>  
  
- <span data-ttu-id="9ecff-119">Nadřazená složka složky, která<xref:System.IO.IOException> má být vytvořena, je jen pro čtení (třída).</span><span class="sxs-lookup"><span data-stu-id="9ecff-119">The parent folder of the folder to be created is read-only (<xref:System.IO.IOException> class).</span></span>  
  
- <span data-ttu-id="9ecff-120">Název složky `null` <xref:System.ArgumentNullException> je (třída).</span><span class="sxs-lookup"><span data-stu-id="9ecff-120">The folder name is `null` (<xref:System.ArgumentNullException> class).</span></span>  
  
- <span data-ttu-id="9ecff-121">Název složky je<xref:System.IO.PathTooLongException> příliš dlouhý (třída).</span><span class="sxs-lookup"><span data-stu-id="9ecff-121">The folder name is too long (<xref:System.IO.PathTooLongException> class).</span></span>  
  
- <span data-ttu-id="9ecff-122">Název složky je pouze dvojtečka, ":"(<xref:System.IO.PathTooLongException> třída).</span><span class="sxs-lookup"><span data-stu-id="9ecff-122">The folder name is only a colon, ":" (<xref:System.IO.PathTooLongException> class).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="9ecff-123">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="9ecff-123">.NET Framework Security</span></span>  
 <span data-ttu-id="9ecff-124">Instance třídy <xref:System.Security.SecurityException> může být vyvolána v situacích částečné důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="9ecff-124">An instance of the <xref:System.Security.SecurityException> class may be thrown in partial-trust situations.</span></span>  
  
 <span data-ttu-id="9ecff-125">Pokud nemáte oprávnění k vytvoření složky, příklad vyvolá instanci <xref:System.UnauthorizedAccessException> třídy.</span><span class="sxs-lookup"><span data-stu-id="9ecff-125">If you don’t have permission to create the folder, the example throws an instance of the <xref:System.UnauthorizedAccessException> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ecff-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="9ecff-126">See also</span></span>

- <xref:System.IO?displayProperty=nameWithType>
- [<span data-ttu-id="9ecff-127">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="9ecff-127">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="9ecff-128">Systém souborů a registr (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="9ecff-128">File System and the Registry (C# Programming Guide)</span></span>](./index.md)
