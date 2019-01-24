---
title: Ordinální číslo není platné.
ms.date: 07/20/2015
f1_keywords:
- vbrID452
ms.assetid: 7459562b-cd4f-4590-95e0-6126ae3589a5
ms.openlocfilehash: 351b7ee7f1cfc5199d878c33965770693227ccc4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54618958"
---
# <a name="ordinal-is-not-valid"></a><span data-ttu-id="683ad-102">Ordinální číslo není platné.</span><span class="sxs-lookup"><span data-stu-id="683ad-102">Ordinal is not valid</span></span>
<span data-ttu-id="683ad-103">Volání dynamická knihovna (DLL) uvedené číslo nahrazujícím název procedury pomocí `#num` syntaxe.</span><span class="sxs-lookup"><span data-stu-id="683ad-103">Your call to a dynamic-link library (DLL) indicated to use a number instead of a procedure name, using the `#num` syntax.</span></span> <span data-ttu-id="683ad-104">Tato chyba má následující možné příčiny:</span><span class="sxs-lookup"><span data-stu-id="683ad-104">This error has the following possible causes:</span></span>  
  
-   <span data-ttu-id="683ad-105">Pokus o převod `#num` výraz, který se ordinální číslo se nezdařil.</span><span class="sxs-lookup"><span data-stu-id="683ad-105">An attempt to convert the `#num` expression to an ordinal failed.</span></span>  
  
-   <span data-ttu-id="683ad-106">`#num` Zadané neurčuje žádné funkce v knihovně DLL.</span><span class="sxs-lookup"><span data-stu-id="683ad-106">The `#num` specified does not specify any function in the DLL.</span></span>  
  
-   <span data-ttu-id="683ad-107">Knihovna typů má neplatnou deklarací výsledkem interní použití neplatné ordinální číslo.</span><span class="sxs-lookup"><span data-stu-id="683ad-107">A type library has an invalid declaration resulting in internal use of an invalid ordinal number.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="683ad-108">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="683ad-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="683ad-109">Ujistěte se, že výraz představuje platné číslo nebo voláním procedury podle názvu.</span><span class="sxs-lookup"><span data-stu-id="683ad-109">Make sure the expression represents a valid number, or call the procedure by name.</span></span>  
  
2.  <span data-ttu-id="683ad-110">Ujistěte se, že `#num` identifikuje platná funkce v knihovně DLL.</span><span class="sxs-lookup"><span data-stu-id="683ad-110">Make sure `#num` identifies a valid function in the DLL.</span></span>  
  
3.  <span data-ttu-id="683ad-111">Vzájemnou izolací volání procedury, které jsou příčinou problému, tak kód.</span><span class="sxs-lookup"><span data-stu-id="683ad-111">Isolate the procedure call causing the problem by commenting out the code.</span></span> <span data-ttu-id="683ad-112">Zápis `Declare` příkaz pro postup a sestavy problém, který chcete dodavatele knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="683ad-112">Write a `Declare` statement for the procedure, and report the problem to the type library vendor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="683ad-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="683ad-113">See also</span></span>
- [<span data-ttu-id="683ad-114">Příkaz Declare</span><span class="sxs-lookup"><span data-stu-id="683ad-114">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)
