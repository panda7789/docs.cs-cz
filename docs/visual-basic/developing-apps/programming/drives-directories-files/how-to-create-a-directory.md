---
title: 'Postupy: Vytvoření adresáře'
ms.date: 07/20/2015
helpviewer_keywords:
- directories [Visual Basic], creating
- folders [Visual Basic], creating
ms.assetid: 0351a2ca-24d8-43b5-bb39-9b99e6401cff
ms.openlocfilehash: 3d838352a0a3dd69a1555dc34b8acba3afba278b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348803"
---
# <a name="how-to-create-a-directory-in-visual-basic"></a><span data-ttu-id="be63d-102">Postupy: Vytvoření adresáře v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="be63d-102">How to: Create a Directory in Visual Basic</span></span>

<span data-ttu-id="be63d-103">K vytvoření adresáře použijte metodu `CreateDirectory` objektu `My.Computer.FileSystem`.</span><span class="sxs-lookup"><span data-stu-id="be63d-103">Use the `CreateDirectory` method of the `My.Computer.FileSystem` object to create directories.</span></span>  
  
 <span data-ttu-id="be63d-104">Pokud adresář již existuje, není vyvolána žádná výjimka.</span><span class="sxs-lookup"><span data-stu-id="be63d-104">If the directory already exists, no exception is thrown.</span></span>  
  
### <a name="to-create-a-directory"></a><span data-ttu-id="be63d-105">Vytvoření adresáře</span><span class="sxs-lookup"><span data-stu-id="be63d-105">To create a directory</span></span>  
  
- <span data-ttu-id="be63d-106">Použijte metodu `CreateDirectory` zadáním úplné cesty k umístění, kde má být adresář vytvořen.</span><span class="sxs-lookup"><span data-stu-id="be63d-106">Use the `CreateDirectory` method by specifying the full path of the location where the directory should be created.</span></span> <span data-ttu-id="be63d-107">Tento příklad vytvoří adresář `NewDirectory` v `C:\Documents and Settings\All Users\Documents`.</span><span class="sxs-lookup"><span data-stu-id="be63d-107">This example creates the directory `NewDirectory` in `C:\Documents and Settings\All Users\Documents`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#2)]  
  
## <a name="robust-programming"></a><span data-ttu-id="be63d-108">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="be63d-108">Robust Programming</span></span>  

 <span data-ttu-id="be63d-109">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="be63d-109">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="be63d-110">Název adresáře je poškozený.</span><span class="sxs-lookup"><span data-stu-id="be63d-110">The directory name is malformed.</span></span> <span data-ttu-id="be63d-111">Například obsahuje neplatné znaky nebo je pouze mezera (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="be63d-111">For example, it contains illegal characters or is only white space (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="be63d-112">Nadřazený adresář adresáře, který se má vytvořit, je jen pro čtení (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="be63d-112">The parent directory of the directory to be created is read-only (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="be63d-113">Název adresáře je `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="be63d-113">The directory name is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="be63d-114">Název adresáře je příliš dlouhý (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="be63d-114">The directory name is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="be63d-115">Název adresáře je dvojtečka ":" (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="be63d-115">The directory name is a colon ":" (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="be63d-116">Uživatel nemá oprávnění k vytvoření adresáře (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="be63d-116">The user does not have permission to create the directory (<xref:System.UnauthorizedAccessException>).</span></span>  
  
- <span data-ttu-id="be63d-117">Uživatel nemá oprávnění v situaci s částečnou důvěryhodností (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="be63d-117">The user lacks permissions in a partial-trust situation (<xref:System.Security.SecurityException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be63d-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="be63d-118">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CreateDirectory%2A>
- [<span data-ttu-id="be63d-119">Vytváření, odstraňování a přesouvání souborů a adresářů</span><span class="sxs-lookup"><span data-stu-id="be63d-119">Creating, Deleting, and Moving Files and Directories</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/creating-deleting-and-moving-files-and-directories.md)
