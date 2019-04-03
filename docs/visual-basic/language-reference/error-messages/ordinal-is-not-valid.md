---
title: Ordinální číslo není platné.
ms.date: 07/20/2015
f1_keywords:
- vbrID452
ms.assetid: 7459562b-cd4f-4590-95e0-6126ae3589a5
ms.openlocfilehash: f3207c2cc237ae22c295c2b3ed56f18601625226
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58822246"
---
# <a name="ordinal-is-not-valid"></a><span data-ttu-id="7db94-102">Ordinální číslo není platné.</span><span class="sxs-lookup"><span data-stu-id="7db94-102">Ordinal is not valid</span></span>
<span data-ttu-id="7db94-103">Volání dynamická knihovna (DLL) uvedené číslo nahrazujícím název procedury pomocí `#num` syntaxe.</span><span class="sxs-lookup"><span data-stu-id="7db94-103">Your call to a dynamic-link library (DLL) indicated to use a number instead of a procedure name, using the `#num` syntax.</span></span> <span data-ttu-id="7db94-104">Tato chyba má následující možné příčiny:</span><span class="sxs-lookup"><span data-stu-id="7db94-104">This error has the following possible causes:</span></span>  
  
-   <span data-ttu-id="7db94-105">Pokus o převod `#num` výraz, který se ordinální číslo se nezdařil.</span><span class="sxs-lookup"><span data-stu-id="7db94-105">An attempt to convert the `#num` expression to an ordinal failed.</span></span>  
  
-   <span data-ttu-id="7db94-106">`#num` Zadané neurčuje žádné funkce v knihovně DLL.</span><span class="sxs-lookup"><span data-stu-id="7db94-106">The `#num` specified does not specify any function in the DLL.</span></span>  
  
-   <span data-ttu-id="7db94-107">Knihovna typů má neplatnou deklarací výsledkem interní použití neplatné ordinální číslo.</span><span class="sxs-lookup"><span data-stu-id="7db94-107">A type library has an invalid declaration resulting in internal use of an invalid ordinal number.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="7db94-108">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="7db94-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="7db94-109">Ujistěte se, že výraz představuje platné číslo nebo voláním procedury podle názvu.</span><span class="sxs-lookup"><span data-stu-id="7db94-109">Make sure the expression represents a valid number, or call the procedure by name.</span></span>  
  
2.  <span data-ttu-id="7db94-110">Ujistěte se, že `#num` identifikuje platná funkce v knihovně DLL.</span><span class="sxs-lookup"><span data-stu-id="7db94-110">Make sure `#num` identifies a valid function in the DLL.</span></span>  
  
3.  <span data-ttu-id="7db94-111">Vzájemnou izolací volání procedury, které jsou příčinou problému, tak kód.</span><span class="sxs-lookup"><span data-stu-id="7db94-111">Isolate the procedure call causing the problem by commenting out the code.</span></span> <span data-ttu-id="7db94-112">Zápis `Declare` příkaz pro postup a sestavy problém, který chcete dodavatele knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="7db94-112">Write a `Declare` statement for the procedure, and report the problem to the type library vendor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7db94-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7db94-113">See also</span></span>

- [<span data-ttu-id="7db94-114">Příkaz Declare</span><span class="sxs-lookup"><span data-stu-id="7db94-114">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)
