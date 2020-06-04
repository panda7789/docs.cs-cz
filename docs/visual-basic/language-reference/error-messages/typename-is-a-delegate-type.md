---
title: "'<typename>' je typ delegátu."
ms.date: 07/20/2015
f1_keywords:
- bc32008
- vbc32008
helpviewer_keywords:
- BC32008
ms.assetid: dc6abba0-a9ad-450f-8899-87265bc84abc
ms.openlocfilehash: 7056bbf2b4de26feba3bfbe0e02b3239311271c9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84382169"
---
# <a name="typename-is-a-delegate-type"></a><span data-ttu-id="3304e-102">'\<typename>' je typ delegátu.</span><span class="sxs-lookup"><span data-stu-id="3304e-102">'\<typename>' is a delegate type</span></span>
<span data-ttu-id="3304e-103">\<typename>je typ delegáta.</span><span class="sxs-lookup"><span data-stu-id="3304e-103">'\<typename>' is a delegate type.</span></span> <span data-ttu-id="3304e-104">Konstrukce delegáta povoluje jako seznam argumentů pouze jeden výraz AddressOf.</span><span class="sxs-lookup"><span data-stu-id="3304e-104">Delegate construction permits only a single AddressOf expression as an argument list.</span></span> <span data-ttu-id="3304e-105">Výraz AddressOf se často dá použít místo konstrukce delegáta.</span><span class="sxs-lookup"><span data-stu-id="3304e-105">Often an AddressOf expression can be used instead of a delegate construction.</span></span>  
  
 <span data-ttu-id="3304e-106">`New`Klauzule vytvářející instanci třídy delegáta poskytuje neplatný seznam argumentů konstruktoru delegáta.</span><span class="sxs-lookup"><span data-stu-id="3304e-106">A `New` clause creating an instance of a delegate class supplies an invalid argument list to the delegate constructor.</span></span>  
  
 <span data-ttu-id="3304e-107">`AddressOf`Při vytváření nové instance delegáta můžete zadávat jenom jeden výraz.</span><span class="sxs-lookup"><span data-stu-id="3304e-107">You can supply only a single `AddressOf` expression when creating a new delegate instance.</span></span>  
  
 <span data-ttu-id="3304e-108">Tato chyba může být způsobena tím, že nepředáte žádné argumenty konstruktoru delegáta, Pokud předáte více než jeden argument, nebo Pokud předáte jeden argument, který není platným `AddressOf` výrazem.</span><span class="sxs-lookup"><span data-stu-id="3304e-108">This error can result if you do not pass any arguments to the delegate constructor, if you pass more than one argument, or if you pass a single argument that is not a valid `AddressOf` expression.</span></span>  
  
 <span data-ttu-id="3304e-109">**ID chyby:** BC32008</span><span class="sxs-lookup"><span data-stu-id="3304e-109">**Error ID:** BC32008</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="3304e-110">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="3304e-110">To correct this error</span></span>  
  
- <span data-ttu-id="3304e-111">`AddressOf`V seznamu argumentů pro třídu Delegate v klauzuli použijte jeden výraz `New` .</span><span class="sxs-lookup"><span data-stu-id="3304e-111">Use a single `AddressOf` expression in the argument list for the delegate class in the `New` clause.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3304e-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="3304e-112">See also</span></span>

- [<span data-ttu-id="3304e-113">New – operátor</span><span class="sxs-lookup"><span data-stu-id="3304e-113">New Operator</span></span>](../operators/new-operator.md)
- [<span data-ttu-id="3304e-114">AddressOf – operátor</span><span class="sxs-lookup"><span data-stu-id="3304e-114">AddressOf Operator</span></span>](../operators/addressof-operator.md)
- [<span data-ttu-id="3304e-115">Delegáti</span><span class="sxs-lookup"><span data-stu-id="3304e-115">Delegates</span></span>](../../programming-guide/language-features/delegates/index.md)
- [<span data-ttu-id="3304e-116">Postupy: Volání metody delegáta</span><span class="sxs-lookup"><span data-stu-id="3304e-116">How to: Invoke a Delegate Method</span></span>](../../programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)
