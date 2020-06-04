---
title: Chyba přístupu k cestě nebo k souboru
ms.date: 07/20/2015
f1_keywords:
- vbrID75
ms.assetid: 6ce3a161-7316-46bd-a785-0d50e5414020
ms.openlocfilehash: dfe96cd6eaa673438849fe8f799d46fa2617bfdd
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84387254"
---
# <a name="pathfile-access-error"></a><span data-ttu-id="eb3ff-102">Chyba přístupu k cestě nebo k souboru</span><span class="sxs-lookup"><span data-stu-id="eb3ff-102">Path/File access error</span></span>
<span data-ttu-id="eb3ff-103">Během operace přístupu k souboru nebo přístupu k disku nemohl operační systém vytvořit spojení mezi cestou a názvem souboru.</span><span class="sxs-lookup"><span data-stu-id="eb3ff-103">During a file-access or disk-access operation, the operating system could not make a connection between the path and the file name.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="eb3ff-104">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="eb3ff-104">To correct this error</span></span>  
  
1. <span data-ttu-id="eb3ff-105">Ujistěte se, že specifikace souboru je správně naformátovaná.</span><span class="sxs-lookup"><span data-stu-id="eb3ff-105">Make sure the file specification is correctly formatted.</span></span> <span data-ttu-id="eb3ff-106">Název souboru může obsahovat plně kvalifikovanou (absolutní) nebo relativní cestu.</span><span class="sxs-lookup"><span data-stu-id="eb3ff-106">A file name can contain a fully qualified (absolute) or relative path.</span></span> <span data-ttu-id="eb3ff-107">Plně kvalifikovaná cesta začíná názvem jednotky (Pokud je cesta na jiné jednotce) a je v ní uvedena explicitní cesta z kořene souboru.</span><span class="sxs-lookup"><span data-stu-id="eb3ff-107">A fully qualified path starts with the drive name (if the path is on another drive) and lists the explicit path from the root to the file.</span></span> <span data-ttu-id="eb3ff-108">Libovolná cesta, která není plně kvalifikovaná, je relativní vzhledem k aktuální jednotce a adresáři.</span><span class="sxs-lookup"><span data-stu-id="eb3ff-108">Any path that is not fully qualified is relative to the current drive and directory.</span></span>  
  
2. <span data-ttu-id="eb3ff-109">Ujistěte se, že jste se nepokoušeli uložit soubor, který by nahradil existující soubor určený jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="eb3ff-109">Make sure that you did not attempt to save a file that would replace an existing read-only file.</span></span> <span data-ttu-id="eb3ff-110">Pokud se jedná o tento případ, změňte atribut jen pro čtení cílového souboru nebo uložte soubor s jiným názvem souboru.</span><span class="sxs-lookup"><span data-stu-id="eb3ff-110">If this is the case, change the read-only attribute of the target file, or save the file with a different file name.</span></span>  
  
3. <span data-ttu-id="eb3ff-111">Ujistěte se, že jste se nepokoušeli otevřít soubor jen pro čtení v sekvenčním `Output` nebo `Append` režimu.</span><span class="sxs-lookup"><span data-stu-id="eb3ff-111">Make sure you did not attempt to open a read-only file in sequential `Output` or `Append` mode.</span></span> <span data-ttu-id="eb3ff-112">Pokud se jedná o tento případ, otevřete soubor v `Input` režimu nebo změňte atribut souboru jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="eb3ff-112">If this is the case, open the file in `Input` mode or change the read-only attribute of the file.</span></span>  
  
4. <span data-ttu-id="eb3ff-113">Ujistěte se, že jste se nepokoušeli změnit Visual Basic projekt v rámci databáze nebo dokumentu.</span><span class="sxs-lookup"><span data-stu-id="eb3ff-113">Make sure you did not attempt to change a Visual Basic project within a database or document.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb3ff-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="eb3ff-114">See also</span></span>

- [<span data-ttu-id="eb3ff-115">Typy chyb</span><span class="sxs-lookup"><span data-stu-id="eb3ff-115">Error Types</span></span>](../../programming-guide/language-features/error-types.md)
