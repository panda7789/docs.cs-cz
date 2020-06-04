---
title: Ordinální číslo není platné.
ms.date: 07/20/2015
f1_keywords:
- vbrID452
ms.assetid: 7459562b-cd4f-4590-95e0-6126ae3589a5
ms.openlocfilehash: 7b9bd8435b56dd5e33d14eb35d76aacc7d60c8b5
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413050"
---
# <a name="ordinal-is-not-valid"></a><span data-ttu-id="ccb76-102">Ordinální číslo není platné.</span><span class="sxs-lookup"><span data-stu-id="ccb76-102">Ordinal is not valid</span></span>
<span data-ttu-id="ccb76-103">Vaše volání dynamické knihovny (DLL) označené k použití čísla namísto názvu procedury, pomocí `#num` syntaxe.</span><span class="sxs-lookup"><span data-stu-id="ccb76-103">Your call to a dynamic-link library (DLL) indicated to use a number instead of a procedure name, using the `#num` syntax.</span></span> <span data-ttu-id="ccb76-104">Tato chyba má následující možné příčiny:</span><span class="sxs-lookup"><span data-stu-id="ccb76-104">This error has the following possible causes:</span></span>  
  
- <span data-ttu-id="ccb76-105">Pokus o převod `#num` výrazu na pořadové číslo se nezdařil.</span><span class="sxs-lookup"><span data-stu-id="ccb76-105">An attempt to convert the `#num` expression to an ordinal failed.</span></span>  
  
- <span data-ttu-id="ccb76-106">`#num`Zadaný parametr neurčuje žádné funkce v knihovně DLL.</span><span class="sxs-lookup"><span data-stu-id="ccb76-106">The `#num` specified does not specify any function in the DLL.</span></span>  
  
- <span data-ttu-id="ccb76-107">Knihovna typů má neplatnou deklaraci, která má za následek interní použití neplatného pořadového čísla.</span><span class="sxs-lookup"><span data-stu-id="ccb76-107">A type library has an invalid declaration resulting in internal use of an invalid ordinal number.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="ccb76-108">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="ccb76-108">To correct this error</span></span>  
  
1. <span data-ttu-id="ccb76-109">Ujistěte se, že výraz představuje platné číslo, nebo zavolejte proceduru podle názvu.</span><span class="sxs-lookup"><span data-stu-id="ccb76-109">Make sure the expression represents a valid number, or call the procedure by name.</span></span>  
  
2. <span data-ttu-id="ccb76-110">Ujistěte se, že `#num` je v knihovně DLL identifikována platná funkce.</span><span class="sxs-lookup"><span data-stu-id="ccb76-110">Make sure `#num` identifies a valid function in the DLL.</span></span>  
  
3. <span data-ttu-id="ccb76-111">Izolujte volání procedury způsobující problém pomocí komentáře kódu.</span><span class="sxs-lookup"><span data-stu-id="ccb76-111">Isolate the procedure call causing the problem by commenting out the code.</span></span> <span data-ttu-id="ccb76-112">Zápis `Declare` příkazu pro proceduru a nahlášení problému na dodavatele knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="ccb76-112">Write a `Declare` statement for the procedure, and report the problem to the type library vendor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ccb76-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="ccb76-113">See also</span></span>

- [<span data-ttu-id="ccb76-114">Declare – příkaz</span><span class="sxs-lookup"><span data-stu-id="ccb76-114">Declare Statement</span></span>](../statements/declare-statement.md)
