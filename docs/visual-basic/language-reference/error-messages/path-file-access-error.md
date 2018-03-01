---
title: "Chyba přístupu k souboru cesta"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID75
ms.assetid: 6ce3a161-7316-46bd-a785-0d50e5414020
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2c86d46c884617be152a5954426e9ddd6ef61651
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="pathfile-access-error"></a><span data-ttu-id="125fc-102">Chyba přístupu k cestě nebo k souboru</span><span class="sxs-lookup"><span data-stu-id="125fc-102">Path/File access error</span></span>
<span data-ttu-id="125fc-103">Během operace přístupu k souborům nebo přístup k disku operačního systému nelze navázat připojení mezi cestu a název souboru.</span><span class="sxs-lookup"><span data-stu-id="125fc-103">During a file-access or disk-access operation, the operating system could not make a connection between the path and the file name.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="125fc-104">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="125fc-104">To correct this error</span></span>  
  
1.  <span data-ttu-id="125fc-105">Zkontrolujte, zda že je správně naformátován specifikaci souboru.</span><span class="sxs-lookup"><span data-stu-id="125fc-105">Make sure the file specification is correctly formatted.</span></span> <span data-ttu-id="125fc-106">Název souboru může obsahovat plně kvalifikovaný (absolutní) nebo relativní cestu.</span><span class="sxs-lookup"><span data-stu-id="125fc-106">A file name can contain a fully qualified (absolute) or relative path.</span></span> <span data-ttu-id="125fc-107">Plně kvalifikovaná cesta začíná název jednotky (Pokud je cesta na jiné jednotce) a zobrazuje explicitní cestu z kořene do souboru.</span><span class="sxs-lookup"><span data-stu-id="125fc-107">A fully qualified path starts with the drive name (if the path is on another drive) and lists the explicit path from the root to the file.</span></span> <span data-ttu-id="125fc-108">Jakoukoli cestu, která není plně kvalifikovaná je relativní vzhledem k aktuální jednotky a adresáře.</span><span class="sxs-lookup"><span data-stu-id="125fc-108">Any path that is not fully qualified is relative to the current drive and directory.</span></span>  
  
2.  <span data-ttu-id="125fc-109">Ujistěte se, že jste se nepokusil uložit soubor, který by nahradit existující soubor jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="125fc-109">Make sure that you did not attempt to save a file that would replace an existing read-only file.</span></span> <span data-ttu-id="125fc-110">Pokud je to tento případ, měnit atribut jen pro čtení cílový soubor a uložte soubor s jiným názvem souboru.</span><span class="sxs-lookup"><span data-stu-id="125fc-110">If this is the case, change the read-only attribute of the target file, or save the file with a different file name.</span></span>  
  
3.  <span data-ttu-id="125fc-111">Zajistěte, aby nepokusil otevřete soubor jen pro čtení v sekvenčních `Output` nebo `Append` režimu.</span><span class="sxs-lookup"><span data-stu-id="125fc-111">Make sure you did not attempt to open a read-only file in sequential `Output` or `Append` mode.</span></span> <span data-ttu-id="125fc-112">Pokud je to tento případ, otevřete soubor v `Input` režimu nebo změnit atribut jen pro čtení souboru.</span><span class="sxs-lookup"><span data-stu-id="125fc-112">If this is the case, open the file in `Input` mode or change the read-only attribute of the file.</span></span>  
  
4.  <span data-ttu-id="125fc-113">Zajistěte, aby pokus o změnu [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] projektu v databázi nebo dokumentu.</span><span class="sxs-lookup"><span data-stu-id="125fc-113">Make sure you did not attempt to change a [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] project within a database or document.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="125fc-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="125fc-114">See Also</span></span>  
 [<span data-ttu-id="125fc-115">Typy chyb</span><span class="sxs-lookup"><span data-stu-id="125fc-115">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)
