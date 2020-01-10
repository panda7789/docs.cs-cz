---
title: Postup vytvoření souboru nebo složky – C# Průvodce programováním
ms.date: 07/20/2015
helpviewer_keywords:
- folders [C#]
- creating files [C#]
- files [C#]
- creating folders [C#]
ms.assetid: 4582ee2d-d72d-4687-bcb9-08d336c62c25
ms.openlocfilehash: e0d0a7fbbc7e6a5c9a0bd00dec1188c5cfdcf896
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705246"
---
# <a name="how-to-create-a-file-or-folder-c-programming-guide"></a><span data-ttu-id="cd286-102">Postup vytvoření souboru nebo složky (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="cd286-102">How to create a file or folder (C# Programming Guide)</span></span>
<span data-ttu-id="cd286-103">Můžete programově vytvořit složku v počítači, vytvořit podsložku, vytvořit soubor v podsložce a zapsat data do souboru.</span><span class="sxs-lookup"><span data-stu-id="cd286-103">You can programmatically create a folder on your computer, create a subfolder, create a file in the subfolder, and write data to the file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cd286-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="cd286-104">Example</span></span>  
 [!code-csharp[csFilesandFolders#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#10)]  
  
 <span data-ttu-id="cd286-105">Pokud složka již existuje, <xref:System.IO.Directory.CreateDirectory%2A> neprovede žádnou akci a není vyvolána žádná výjimka.</span><span class="sxs-lookup"><span data-stu-id="cd286-105">If the folder already exists, <xref:System.IO.Directory.CreateDirectory%2A> does nothing, and no exception is thrown.</span></span> <span data-ttu-id="cd286-106"><xref:System.IO.File.Create%2A?displayProperty=nameWithType> však nahradí existující soubor novým souborem.</span><span class="sxs-lookup"><span data-stu-id="cd286-106">However, <xref:System.IO.File.Create%2A?displayProperty=nameWithType> replaces an existing file with a new file.</span></span> <span data-ttu-id="cd286-107">V příkladu se používá příkaz `if`-`else`, který brání v nahrazení existujícího souboru.</span><span class="sxs-lookup"><span data-stu-id="cd286-107">The example uses an `if`-`else` statement to prevent an existing file from being replaced.</span></span>  
  
 <span data-ttu-id="cd286-108">Provedením následujících změn v příkladu můžete určit různé výsledky na základě toho, zda soubor s určitým názvem již existuje.</span><span class="sxs-lookup"><span data-stu-id="cd286-108">By making the following changes in the example, you can specify different outcomes based on whether a file with a certain name already exists.</span></span> <span data-ttu-id="cd286-109">Pokud takový soubor neexistuje, kód ho vytvoří.</span><span class="sxs-lookup"><span data-stu-id="cd286-109">If such a file doesn't exist, the code creates one.</span></span> <span data-ttu-id="cd286-110">Pokud takový soubor existuje, kód připojí data do tohoto souboru.</span><span class="sxs-lookup"><span data-stu-id="cd286-110">If such a file exists, the code appends data to that file.</span></span>  
  
- <span data-ttu-id="cd286-111">Zadejte jiný než náhodný název souboru.</span><span class="sxs-lookup"><span data-stu-id="cd286-111">Specify a non-random file name.</span></span>  
  
    ```csharp  
    // Comment out the following line.  
    //string fileName = System.IO.Path.GetRandomFileName();  
  
    // Replace that line with the following assignment.  
    string fileName = "MyNewFile.txt";  
    ```  
  
- <span data-ttu-id="cd286-112">V následujícím kódu nahraďte příkaz `if`-`else` příkazem `using`.</span><span class="sxs-lookup"><span data-stu-id="cd286-112">Replace the `if`-`else` statement with the `using` statement in the following code.</span></span>  
  
    ```csharp  
    using (System.IO.FileStream fs = new System.IO.FileStream(pathString, FileMode.Append))   
    {  
        for (byte i = 0; i < 100; i++)  
        {  
            fs.WriteByte(i);  
        }  
    }  
    ```  
  
 <span data-ttu-id="cd286-113">Spusťte příklad několikrát, abyste ověřili, že se data do souboru přidávají pokaždé.</span><span class="sxs-lookup"><span data-stu-id="cd286-113">Run the example several times to verify that data is added to the file each time.</span></span>  
  
 <span data-ttu-id="cd286-114">Další `FileMode` hodnoty, které můžete vyzkoušet, najdete v tématu <xref:System.IO.FileMode>.</span><span class="sxs-lookup"><span data-stu-id="cd286-114">For more `FileMode` values that you can try, see <xref:System.IO.FileMode>.</span></span>  
  
 <span data-ttu-id="cd286-115">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="cd286-115">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="cd286-116">Název složky je poškozený.</span><span class="sxs-lookup"><span data-stu-id="cd286-116">The folder name is malformed.</span></span> <span data-ttu-id="cd286-117">Například obsahuje neplatné znaky nebo je pouze mezera (<xref:System.ArgumentException> třídy).</span><span class="sxs-lookup"><span data-stu-id="cd286-117">For example, it contains illegal characters or is only white space (<xref:System.ArgumentException> class).</span></span> <span data-ttu-id="cd286-118">K vytvoření platných názvů cest použijte třídu <xref:System.IO.Path>.</span><span class="sxs-lookup"><span data-stu-id="cd286-118">Use the <xref:System.IO.Path> class to create valid path names.</span></span>  
  
- <span data-ttu-id="cd286-119">Nadřazená složka složky, která se má vytvořit, je jen pro čtení (<xref:System.IO.IOException> třída).</span><span class="sxs-lookup"><span data-stu-id="cd286-119">The parent folder of the folder to be created is read-only (<xref:System.IO.IOException> class).</span></span>  
  
- <span data-ttu-id="cd286-120">Název složky je `null` (<xref:System.ArgumentNullException> třídy).</span><span class="sxs-lookup"><span data-stu-id="cd286-120">The folder name is `null` (<xref:System.ArgumentNullException> class).</span></span>  
  
- <span data-ttu-id="cd286-121">Název složky je příliš dlouhý (<xref:System.IO.PathTooLongException> třídy).</span><span class="sxs-lookup"><span data-stu-id="cd286-121">The folder name is too long (<xref:System.IO.PathTooLongException> class).</span></span>  
  
- <span data-ttu-id="cd286-122">Název složky je pouze dvojtečka, ":" (<xref:System.IO.PathTooLongException> třídy).</span><span class="sxs-lookup"><span data-stu-id="cd286-122">The folder name is only a colon, ":" (<xref:System.IO.PathTooLongException> class).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="cd286-123">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="cd286-123">.NET Framework Security</span></span>  
 <span data-ttu-id="cd286-124">Instance <xref:System.Security.SecurityException> třídy může být vyvolána v situacích částečné důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="cd286-124">An instance of the <xref:System.Security.SecurityException> class may be thrown in partial-trust situations.</span></span>  
  
 <span data-ttu-id="cd286-125">Pokud nemáte oprávnění k vytvoření složky, příklad vyvolá instanci třídy <xref:System.UnauthorizedAccessException>.</span><span class="sxs-lookup"><span data-stu-id="cd286-125">If you don’t have permission to create the folder, the example throws an instance of the <xref:System.UnauthorizedAccessException> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd286-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cd286-126">See also</span></span>

- <xref:System.IO?displayProperty=nameWithType>
- [<span data-ttu-id="cd286-127">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="cd286-127">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="cd286-128">Systém souborů a registr (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="cd286-128">File System and the Registry (C# Programming Guide)</span></span>](./index.md)
