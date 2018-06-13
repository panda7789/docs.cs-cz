---
title: Chyba přístupu k souboru cesta
ms.date: 07/20/2015
f1_keywords:
- vbrID75
ms.assetid: 6ce3a161-7316-46bd-a785-0d50e5414020
ms.openlocfilehash: 83ce8615b173a6f5835347ebc561a793655ec8f7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33598580"
---
# <a name="pathfile-access-error"></a><span data-ttu-id="33a65-102">Chyba přístupu k cestě nebo k souboru</span><span class="sxs-lookup"><span data-stu-id="33a65-102">Path/File access error</span></span>
<span data-ttu-id="33a65-103">Během operace přístupu k souborům nebo přístup k disku operačního systému nelze navázat připojení mezi cestu a název souboru.</span><span class="sxs-lookup"><span data-stu-id="33a65-103">During a file-access or disk-access operation, the operating system could not make a connection between the path and the file name.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="33a65-104">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="33a65-104">To correct this error</span></span>  
  
1.  <span data-ttu-id="33a65-105">Zkontrolujte, zda že je správně naformátován specifikaci souboru.</span><span class="sxs-lookup"><span data-stu-id="33a65-105">Make sure the file specification is correctly formatted.</span></span> <span data-ttu-id="33a65-106">Název souboru může obsahovat plně kvalifikovaný (absolutní) nebo relativní cestu.</span><span class="sxs-lookup"><span data-stu-id="33a65-106">A file name can contain a fully qualified (absolute) or relative path.</span></span> <span data-ttu-id="33a65-107">Plně kvalifikovaná cesta začíná název jednotky (Pokud je cesta na jiné jednotce) a zobrazuje explicitní cestu z kořene do souboru.</span><span class="sxs-lookup"><span data-stu-id="33a65-107">A fully qualified path starts with the drive name (if the path is on another drive) and lists the explicit path from the root to the file.</span></span> <span data-ttu-id="33a65-108">Jakoukoli cestu, která není plně kvalifikovaná je relativní vzhledem k aktuální jednotky a adresáře.</span><span class="sxs-lookup"><span data-stu-id="33a65-108">Any path that is not fully qualified is relative to the current drive and directory.</span></span>  
  
2.  <span data-ttu-id="33a65-109">Ujistěte se, že jste se nepokusil uložit soubor, který by nahradit existující soubor jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="33a65-109">Make sure that you did not attempt to save a file that would replace an existing read-only file.</span></span> <span data-ttu-id="33a65-110">Pokud je to tento případ, měnit atribut jen pro čtení cílový soubor a uložte soubor s jiným názvem souboru.</span><span class="sxs-lookup"><span data-stu-id="33a65-110">If this is the case, change the read-only attribute of the target file, or save the file with a different file name.</span></span>  
  
3.  <span data-ttu-id="33a65-111">Zajistěte, aby nepokusil otevřete soubor jen pro čtení v sekvenčních `Output` nebo `Append` režimu.</span><span class="sxs-lookup"><span data-stu-id="33a65-111">Make sure you did not attempt to open a read-only file in sequential `Output` or `Append` mode.</span></span> <span data-ttu-id="33a65-112">Pokud je to tento případ, otevřete soubor v `Input` režimu nebo změnit atribut jen pro čtení souboru.</span><span class="sxs-lookup"><span data-stu-id="33a65-112">If this is the case, open the file in `Input` mode or change the read-only attribute of the file.</span></span>  
  
4.  <span data-ttu-id="33a65-113">Zajistěte, aby že nepokusil změnit projektu jazyka Visual Basic v databázi nebo dokumentu.</span><span class="sxs-lookup"><span data-stu-id="33a65-113">Make sure you did not attempt to change a Visual Basic project within a database or document.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33a65-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="33a65-114">See Also</span></span>  
 [<span data-ttu-id="33a65-115">Typy chyb</span><span class="sxs-lookup"><span data-stu-id="33a65-115">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)
