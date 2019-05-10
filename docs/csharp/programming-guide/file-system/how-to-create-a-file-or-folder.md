---
title: 'Postupy: Vytvoření souboru nebo složky - C# Průvodce programováním'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- folders [C#]
- creating files [C#]
- files [C#]
- creating folders [C#]
ms.assetid: 4582ee2d-d72d-4687-bcb9-08d336c62c25
ms.openlocfilehash: 3163598de5d03bf1691379cddae031841b9865d6
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64595642"
---
# <a name="how-to-create-a-file-or-folder-c-programming-guide"></a><span data-ttu-id="bf263-102">Postupy: Vytvoření souboru nebo složky (C# Průvodce programováním v)</span><span class="sxs-lookup"><span data-stu-id="bf263-102">How to: Create a File or Folder (C# Programming Guide)</span></span>
<span data-ttu-id="bf263-103">Můžete prostřednictvím kódu programu vytvořte složku v počítači, vytvořte podsložku, vytvořit soubor v podsložce a zapisovat data do souboru.</span><span class="sxs-lookup"><span data-stu-id="bf263-103">You can programmatically create a folder on your computer, create a subfolder, create a file in the subfolder, and write data to the file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bf263-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="bf263-104">Example</span></span>  
 [!code-csharp[csFilesandFolders#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#10)]  
  
 <span data-ttu-id="bf263-105">Pokud složka již existuje, <xref:System.IO.Directory.CreateDirectory%2A> fakturuje se nic a žádná výjimka je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="bf263-105">If the folder already exists, <xref:System.IO.Directory.CreateDirectory%2A> does nothing, and no exception is thrown.</span></span> <span data-ttu-id="bf263-106">Ale <xref:System.IO.File.Create%2A?displayProperty=nameWithType> nahradí existující soubor do nového souboru.</span><span class="sxs-lookup"><span data-stu-id="bf263-106">However, <xref:System.IO.File.Create%2A?displayProperty=nameWithType> replaces an existing file with a new file.</span></span> <span data-ttu-id="bf263-107">V příkladu se používá `if` - `else` příkaz zabránit nahrazuje existující soubor.</span><span class="sxs-lookup"><span data-stu-id="bf263-107">The example uses an `if`-`else` statement to prevent an existing file from being replaced.</span></span>  
  
 <span data-ttu-id="bf263-108">Provedením následujících změn v příkladu, můžete určit různé výsledky založené na tom, jestli soubor s určitým názvem již existuje.</span><span class="sxs-lookup"><span data-stu-id="bf263-108">By making the following changes in the example, you can specify different outcomes based on whether a file with a certain name already exists.</span></span> <span data-ttu-id="bf263-109">Pokud takový soubor neexistuje, kód ho vytvoří.</span><span class="sxs-lookup"><span data-stu-id="bf263-109">If such a file doesn't exist, the code creates one.</span></span> <span data-ttu-id="bf263-110">Pokud takový soubor existuje, kód připojí data do tohoto souboru.</span><span class="sxs-lookup"><span data-stu-id="bf263-110">If such a file exists, the code appends data to that file.</span></span>  
  
- <span data-ttu-id="bf263-111">Zadejte nenáhodný název.</span><span class="sxs-lookup"><span data-stu-id="bf263-111">Specify a non-random file name.</span></span>  
  
    ```csharp  
    // Comment out the following line.  
    //string fileName = System.IO.Path.GetRandomFileName();  
  
    // Replace that line with the following assignment.  
    string fileName = "MyNewFile.txt";  
    ```  
  
- <span data-ttu-id="bf263-112">Nahradit `if` - `else` příkaz `using` příkaz v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="bf263-112">Replace the `if`-`else` statement with the `using` statement in the following code.</span></span>  
  
    ```csharp  
    using (System.IO.FileStream fs = new System.IO.FileStream(pathString, FileMode.Append))   
    {  
        for (byte i = 0; i < 100; i++)  
        {  
            fs.WriteByte(i);  
        }  
    }  
    ```  
  
 <span data-ttu-id="bf263-113">Spusťte příklad několikrát ověření tato data se přidá do souboru pokaždé, když.</span><span class="sxs-lookup"><span data-stu-id="bf263-113">Run the example several times to verify that data is added to the file each time.</span></span>  
  
 <span data-ttu-id="bf263-114">Další informace `FileMode` hodnoty, které můžete vyzkoušet, naleznete v tématu <xref:System.IO.FileMode>.</span><span class="sxs-lookup"><span data-stu-id="bf263-114">For more `FileMode` values that you can try, see <xref:System.IO.FileMode>.</span></span>  
  
 <span data-ttu-id="bf263-115">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="bf263-115">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="bf263-116">Název složky je chybný.</span><span class="sxs-lookup"><span data-stu-id="bf263-116">The folder name is malformed.</span></span> <span data-ttu-id="bf263-117">Například obsahuje neplatné znaky nebo je prázdné znaky (<xref:System.ArgumentException> třídy).</span><span class="sxs-lookup"><span data-stu-id="bf263-117">For example, it contains illegal characters or is only white space (<xref:System.ArgumentException> class).</span></span> <span data-ttu-id="bf263-118">Použití <xref:System.IO.Path> třídy za účelem vytvoření platné názvy cesty.</span><span class="sxs-lookup"><span data-stu-id="bf263-118">Use the <xref:System.IO.Path> class to create valid path names.</span></span>  
  
- <span data-ttu-id="bf263-119">Nadřazená složka složky, který se má vytvořit je jen pro čtení (<xref:System.IO.IOException> třídy).</span><span class="sxs-lookup"><span data-stu-id="bf263-119">The parent folder of the folder to be created is read-only (<xref:System.IO.IOException> class).</span></span>  
  
- <span data-ttu-id="bf263-120">Název složky je `null` (<xref:System.ArgumentNullException> třídy).</span><span class="sxs-lookup"><span data-stu-id="bf263-120">The folder name is `null` (<xref:System.ArgumentNullException> class).</span></span>  
  
- <span data-ttu-id="bf263-121">Název složky je příliš dlouhý (<xref:System.IO.PathTooLongException> třídy).</span><span class="sxs-lookup"><span data-stu-id="bf263-121">The folder name is too long (<xref:System.IO.PathTooLongException> class).</span></span>  
  
- <span data-ttu-id="bf263-122">Název složky je pouze dvojtečka ":" (<xref:System.IO.PathTooLongException> třídy).</span><span class="sxs-lookup"><span data-stu-id="bf263-122">The folder name is only a colon, ":" (<xref:System.IO.PathTooLongException> class).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="bf263-123">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="bf263-123">.NET Framework Security</span></span>  
 <span data-ttu-id="bf263-124">Instance <xref:System.Security.SecurityException> třídy může být vyvolána v situacích částečné důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="bf263-124">An instance of the <xref:System.Security.SecurityException> class may be thrown in partial-trust situations.</span></span>  
  
 <span data-ttu-id="bf263-125">Pokud nemáte oprávnění k vytvoření složky, příklad vyvolá instanci <xref:System.UnauthorizedAccessException> třídy.</span><span class="sxs-lookup"><span data-stu-id="bf263-125">If you don’t have permission to create the folder, the example throws an instance of the <xref:System.UnauthorizedAccessException> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf263-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bf263-126">See also</span></span>

- <xref:System.IO?displayProperty=nameWithType>
- [<span data-ttu-id="bf263-127">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="bf263-127">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="bf263-128">Systém souborů a registr (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="bf263-128">File System and the Registry (C# Programming Guide)</span></span>](../../../csharp/programming-guide/file-system/index.md)
