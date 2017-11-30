---
title: "Ordinální číslo není platné."
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID452
ms.assetid: 7459562b-cd4f-4590-95e0-6126ae3589a5
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d31d0fba19cc16004c0b56786af30603d0c509ea
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="ordinal-is-not-valid"></a><span data-ttu-id="2af51-102">Ordinální číslo není platné.</span><span class="sxs-lookup"><span data-stu-id="2af51-102">Ordinal is not valid</span></span>
<span data-ttu-id="2af51-103">Volání do dynamická knihovna (DLL) uvedené pro použití číslo místo názvu postup pomocí `#num` syntaxe.</span><span class="sxs-lookup"><span data-stu-id="2af51-103">Your call to a dynamic-link library (DLL) indicated to use a number instead of a procedure name, using the `#num` syntax.</span></span> <span data-ttu-id="2af51-104">Tato chyba má následující možné příčiny:</span><span class="sxs-lookup"><span data-stu-id="2af51-104">This error has the following possible causes:</span></span>  
  
-   <span data-ttu-id="2af51-105">Pokus o převést `#num` výraz, který má pořadí se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="2af51-105">An attempt to convert the `#num` expression to an ordinal failed.</span></span>  
  
-   <span data-ttu-id="2af51-106">`#num` Zadaný v knihovně DLL neurčuje žádné funkce.</span><span class="sxs-lookup"><span data-stu-id="2af51-106">The `#num` specified does not specify any function in the DLL.</span></span>  
  
-   <span data-ttu-id="2af51-107">Knihovny typů obsahuje neplatný deklaraci výsledkem interní použití neplatné číslo pořadí.</span><span class="sxs-lookup"><span data-stu-id="2af51-107">A type library has an invalid declaration resulting in internal use of an invalid ordinal number.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="2af51-108">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="2af51-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="2af51-109">Zkontrolujte, zda že výraz představuje platné číslo nebo voláním procedury podle názvu.</span><span class="sxs-lookup"><span data-stu-id="2af51-109">Make sure the expression represents a valid number, or call the procedure by name.</span></span>  
  
2.  <span data-ttu-id="2af51-110">Zajistěte, aby `#num` identifikuje platnou funkcí v knihovně DLL.</span><span class="sxs-lookup"><span data-stu-id="2af51-110">Make sure `#num` identifies a valid function in the DLL.</span></span>  
  
3.  <span data-ttu-id="2af51-111">Izolujte volání procedury příčinou problému pomocí komentářů si kód.</span><span class="sxs-lookup"><span data-stu-id="2af51-111">Isolate the procedure call causing the problem by commenting out the code.</span></span> <span data-ttu-id="2af51-112">Zápis `Declare` příkaz pro postup a sestava tyto potíže k dodavatele knihovny typu.</span><span class="sxs-lookup"><span data-stu-id="2af51-112">Write a `Declare` statement for the procedure, and report the problem to the type library vendor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2af51-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="2af51-113">See Also</span></span>  
 [<span data-ttu-id="2af51-114">Declare – příkaz</span><span class="sxs-lookup"><span data-stu-id="2af51-114">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)
