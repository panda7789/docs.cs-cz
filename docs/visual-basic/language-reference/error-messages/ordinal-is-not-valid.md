---
title: Ordinální číslo není platné.
ms.date: 07/20/2015
f1_keywords:
- vbrID452
ms.assetid: 7459562b-cd4f-4590-95e0-6126ae3589a5
ms.openlocfilehash: 12d73b33e3c025b40c98d84e3507af7be1e1e91a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33593600"
---
# <a name="ordinal-is-not-valid"></a><span data-ttu-id="1efa2-102">Ordinální číslo není platné.</span><span class="sxs-lookup"><span data-stu-id="1efa2-102">Ordinal is not valid</span></span>
<span data-ttu-id="1efa2-103">Volání do dynamická knihovna (DLL) uvedené pro použití číslo místo názvu postup pomocí `#num` syntaxe.</span><span class="sxs-lookup"><span data-stu-id="1efa2-103">Your call to a dynamic-link library (DLL) indicated to use a number instead of a procedure name, using the `#num` syntax.</span></span> <span data-ttu-id="1efa2-104">Tato chyba má následující možné příčiny:</span><span class="sxs-lookup"><span data-stu-id="1efa2-104">This error has the following possible causes:</span></span>  
  
-   <span data-ttu-id="1efa2-105">Pokus o převést `#num` výraz, který má pořadí se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="1efa2-105">An attempt to convert the `#num` expression to an ordinal failed.</span></span>  
  
-   <span data-ttu-id="1efa2-106">`#num` Zadaný v knihovně DLL neurčuje žádné funkce.</span><span class="sxs-lookup"><span data-stu-id="1efa2-106">The `#num` specified does not specify any function in the DLL.</span></span>  
  
-   <span data-ttu-id="1efa2-107">Knihovny typů obsahuje neplatný deklaraci výsledkem interní použití neplatné číslo pořadí.</span><span class="sxs-lookup"><span data-stu-id="1efa2-107">A type library has an invalid declaration resulting in internal use of an invalid ordinal number.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="1efa2-108">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="1efa2-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="1efa2-109">Zkontrolujte, zda že výraz představuje platné číslo nebo voláním procedury podle názvu.</span><span class="sxs-lookup"><span data-stu-id="1efa2-109">Make sure the expression represents a valid number, or call the procedure by name.</span></span>  
  
2.  <span data-ttu-id="1efa2-110">Zajistěte, aby `#num` identifikuje platnou funkcí v knihovně DLL.</span><span class="sxs-lookup"><span data-stu-id="1efa2-110">Make sure `#num` identifies a valid function in the DLL.</span></span>  
  
3.  <span data-ttu-id="1efa2-111">Izolujte volání procedury příčinou problému pomocí komentářů si kód.</span><span class="sxs-lookup"><span data-stu-id="1efa2-111">Isolate the procedure call causing the problem by commenting out the code.</span></span> <span data-ttu-id="1efa2-112">Zápis `Declare` příkaz pro postup a sestava tyto potíže k dodavatele knihovny typu.</span><span class="sxs-lookup"><span data-stu-id="1efa2-112">Write a `Declare` statement for the procedure, and report the problem to the type library vendor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1efa2-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="1efa2-113">See Also</span></span>  
 [<span data-ttu-id="1efa2-114">Příkaz Declare</span><span class="sxs-lookup"><span data-stu-id="1efa2-114">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)
