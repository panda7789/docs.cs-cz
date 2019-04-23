---
title: Chyba přístupu k souboru v cestě
ms.date: 07/20/2015
f1_keywords:
- vbrID75
ms.assetid: 6ce3a161-7316-46bd-a785-0d50e5414020
ms.openlocfilehash: 4f18c9216aa24840bc205534a97124d12698cb98
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59342151"
---
# <a name="pathfile-access-error"></a><span data-ttu-id="750cc-102">Chyba přístupu k cestě nebo k souboru</span><span class="sxs-lookup"><span data-stu-id="750cc-102">Path/File access error</span></span>
<span data-ttu-id="750cc-103">Během operace přístupu k souborům nebo přístup k disku operačního systému nelze provést připojení mezi cestu a název souboru.</span><span class="sxs-lookup"><span data-stu-id="750cc-103">During a file-access or disk-access operation, the operating system could not make a connection between the path and the file name.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="750cc-104">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="750cc-104">To correct this error</span></span>  
  
1. <span data-ttu-id="750cc-105">Ujistěte se, že je správně naformátován specifikace souboru.</span><span class="sxs-lookup"><span data-stu-id="750cc-105">Make sure the file specification is correctly formatted.</span></span> <span data-ttu-id="750cc-106">Název souboru může obsahovat plně kvalifikovanou (absolutní) nebo relativní cestu.</span><span class="sxs-lookup"><span data-stu-id="750cc-106">A file name can contain a fully qualified (absolute) or relative path.</span></span> <span data-ttu-id="750cc-107">Plně kvalifikovaná cesta začíná název jednotky (Pokud se cesta na jiné jednotce) a seznamy explicitních cestu z kořene do souboru.</span><span class="sxs-lookup"><span data-stu-id="750cc-107">A fully qualified path starts with the drive name (if the path is on another drive) and lists the explicit path from the root to the file.</span></span> <span data-ttu-id="750cc-108">Jakoukoli cestu, která není plně kvalifikovaný je relativní vzhledem k aktuální jednotky a adresáře.</span><span class="sxs-lookup"><span data-stu-id="750cc-108">Any path that is not fully qualified is relative to the current drive and directory.</span></span>  
  
2. <span data-ttu-id="750cc-109">Ujistěte se, že jste se nepokusil uložit soubor, který by nahradit stávající soubor jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="750cc-109">Make sure that you did not attempt to save a file that would replace an existing read-only file.</span></span> <span data-ttu-id="750cc-110">Pokud je to tento případ, změnit atribut jen pro čtení cílový soubor nebo uložte soubor s jiným názvem souboru.</span><span class="sxs-lookup"><span data-stu-id="750cc-110">If this is the case, change the read-only attribute of the target file, or save the file with a different file name.</span></span>  
  
3. <span data-ttu-id="750cc-111">Ujistěte se, že nepokusil otevřít soubor jen pro čtení v sekvenčních `Output` nebo `Append` režimu.</span><span class="sxs-lookup"><span data-stu-id="750cc-111">Make sure you did not attempt to open a read-only file in sequential `Output` or `Append` mode.</span></span> <span data-ttu-id="750cc-112">Pokud je to tento případ, otevřete ho v `Input` režimu nebo změnit atribut jen pro čtení souboru.</span><span class="sxs-lookup"><span data-stu-id="750cc-112">If this is the case, open the file in `Input` mode or change the read-only attribute of the file.</span></span>  
  
4. <span data-ttu-id="750cc-113">Ujistěte se, že se že nepokusil změnit projekt jazyka Visual Basic v databázi nebo dokumentu.</span><span class="sxs-lookup"><span data-stu-id="750cc-113">Make sure you did not attempt to change a Visual Basic project within a database or document.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="750cc-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="750cc-114">See also</span></span>

- [<span data-ttu-id="750cc-115">Typy chyb</span><span class="sxs-lookup"><span data-stu-id="750cc-115">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)
