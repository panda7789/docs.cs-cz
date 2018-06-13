---
title: WriteOnly (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- WriteOnly
- vb.WriteOnly
helpviewer_keywords:
- write-only properties
- WriteOnly keyword [Visual Basic]
- sensitive data, protecting
- properties [Visual Basic], write-only
- sensitive data
ms.assetid: 488d2899-b09f-4cee-92f0-6f9f9fc4f944
ms.openlocfilehash: 4f34f7f4ada3f8d61c9d855eab1b8b073a3d5ed8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33599200"
---
# <a name="writeonly-visual-basic"></a><span data-ttu-id="8e7e7-102">WriteOnly (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8e7e7-102">WriteOnly (Visual Basic)</span></span>
<span data-ttu-id="8e7e7-103">Určuje, že vlastnost může být zapsána ale číst.</span><span class="sxs-lookup"><span data-stu-id="8e7e7-103">Specifies that a property can be written but not read.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8e7e7-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8e7e7-104">Remarks</span></span>  
  
## <a name="rules"></a><span data-ttu-id="8e7e7-105">Pravidla</span><span class="sxs-lookup"><span data-stu-id="8e7e7-105">Rules</span></span>  
 <span data-ttu-id="8e7e7-106">**Kontext deklarace.**</span><span class="sxs-lookup"><span data-stu-id="8e7e7-106">**Declaration Context.**</span></span> <span data-ttu-id="8e7e7-107">Můžete použít `WriteOnly` jenom na úrovni modulu.</span><span class="sxs-lookup"><span data-stu-id="8e7e7-107">You can use `WriteOnly` only at module level.</span></span> <span data-ttu-id="8e7e7-108">To znamená kontext deklarace `WriteOnly` vlastnost musí být třída, struktura nebo modul a nemůže být zdrojový soubor, obor názvů nebo postupu.</span><span class="sxs-lookup"><span data-stu-id="8e7e7-108">This means the declaration context for a `WriteOnly` property must be a class, structure, or module, and cannot be a source file, namespace, or procedure.</span></span>  
  
 <span data-ttu-id="8e7e7-109">Je možné deklarovat vlastnost jako `WriteOnly`, ale nikoli proměnné.</span><span class="sxs-lookup"><span data-stu-id="8e7e7-109">You can declare a property as `WriteOnly`, but not a variable.</span></span>  
  
## <a name="when-to-use-writeonly"></a><span data-ttu-id="8e7e7-110">Kdy použít WriteOnly</span><span class="sxs-lookup"><span data-stu-id="8e7e7-110">When to Use WriteOnly</span></span>  
 <span data-ttu-id="8e7e7-111">Někdy budete chtít kód náročné být schopni nastavit hodnotu, ale není zjistit, co je.</span><span class="sxs-lookup"><span data-stu-id="8e7e7-111">Sometimes you want the consuming code to be able to set a value but not discover what it is.</span></span> <span data-ttu-id="8e7e7-112">Například citlivých dat, jako je sociální číslo registrací nebo heslo, musí být chráněny před přístupem jakékoli součásti, která není nastavena.</span><span class="sxs-lookup"><span data-stu-id="8e7e7-112">For example, sensitive data, such as a social registration number or a password, needs to be protected from access by any component that did not set it.</span></span> <span data-ttu-id="8e7e7-113">V těchto případech můžete použít `WriteOnly` vlastnost na hodnotu.</span><span class="sxs-lookup"><span data-stu-id="8e7e7-113">In these cases, you can use a `WriteOnly` property to set the value.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="8e7e7-114">Pokud definice a používání `WriteOnly` vlastnost, zvažte následující další ochranná opatření:</span><span class="sxs-lookup"><span data-stu-id="8e7e7-114">When you define and use a `WriteOnly` property, consider the following additional protective measures:</span></span>  
  
-   <span data-ttu-id="8e7e7-115">**Přepsání.**</span><span class="sxs-lookup"><span data-stu-id="8e7e7-115">**Overriding.**</span></span> <span data-ttu-id="8e7e7-116">Pokud vlastnost člena třídy, aby ji bylo výchozí [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)a jeho nedeklarujte `Overridable` nebo `MustOverride`.</span><span class="sxs-lookup"><span data-stu-id="8e7e7-116">If the property is a member of a class, allow it to default to [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md), and do not declare it `Overridable` or `MustOverride`.</span></span> <span data-ttu-id="8e7e7-117">Odvozené třídy zabrání provedení nežádoucí přístup pomocí přepsání.</span><span class="sxs-lookup"><span data-stu-id="8e7e7-117">This prevents a derived class from making undesired access through an override.</span></span>  
  
-   <span data-ttu-id="8e7e7-118">**Úroveň přístupu.**</span><span class="sxs-lookup"><span data-stu-id="8e7e7-118">**Access Level.**</span></span> <span data-ttu-id="8e7e7-119">Pokud v jedné nebo více proměnných obsahovat vlastnosti citlivá data, je deklarovat [privátní](../../../visual-basic/language-reference/modifiers/private.md) , aby žádný jiný kód přístup.</span><span class="sxs-lookup"><span data-stu-id="8e7e7-119">If you hold the property's sensitive data in one or more variables, declare them [Private](../../../visual-basic/language-reference/modifiers/private.md) so that no other code can access them.</span></span>  
  
-   <span data-ttu-id="8e7e7-120">**Šifrování.**</span><span class="sxs-lookup"><span data-stu-id="8e7e7-120">**Encryption.**</span></span> <span data-ttu-id="8e7e7-121">Ukládat všechny citlivá data v šifrované podobě, ne ve formátu prostého textu.</span><span class="sxs-lookup"><span data-stu-id="8e7e7-121">Store all sensitive data in encrypted form rather than in plain text.</span></span> <span data-ttu-id="8e7e7-122">Pokud škodlivý kód nějakým způsobem získá přístup k této oblasti paměti, je obtížnější Chcete-li použít data.</span><span class="sxs-lookup"><span data-stu-id="8e7e7-122">If malicious code somehow gains access to that area of memory, it is more difficult to make use of the data.</span></span> <span data-ttu-id="8e7e7-123">Šifrování je také užitečné, pokud je potřeba serializovat citlivá data.</span><span class="sxs-lookup"><span data-stu-id="8e7e7-123">Encryption is also useful if it is necessary to serialize the sensitive data.</span></span>  
  
-   <span data-ttu-id="8e7e7-124">**Resetování.**</span><span class="sxs-lookup"><span data-stu-id="8e7e7-124">**Resetting.**</span></span> <span data-ttu-id="8e7e7-125">Když je ukončovány třídy, struktury nebo modul definování vlastnosti, obnovit důvěrné osobní údaje, výchozí hodnoty nebo na jiné smysl hodnoty.</span><span class="sxs-lookup"><span data-stu-id="8e7e7-125">When the class, structure, or module defining the property is being terminated, reset the sensitive data to default values or to other meaningless values.</span></span> <span data-ttu-id="8e7e7-126">To dává zvláštní ochranu při této oblasti paměti uvolněna pro obecné přístup.</span><span class="sxs-lookup"><span data-stu-id="8e7e7-126">This gives extra protection when that area of memory is freed for general access.</span></span>  
  
-   <span data-ttu-id="8e7e7-127">**Trvalost.**</span><span class="sxs-lookup"><span data-stu-id="8e7e7-127">**Persistence.**</span></span> <span data-ttu-id="8e7e7-128">Pokud ho se můžete vyhnout se nezachovají citlivé údaje, například na disku.</span><span class="sxs-lookup"><span data-stu-id="8e7e7-128">Do not persist any sensitive data, for example on disk, if you can avoid it.</span></span> <span data-ttu-id="8e7e7-129">Navíc Nezapisovat citlivé údaje do schránky.</span><span class="sxs-lookup"><span data-stu-id="8e7e7-129">Also, do not write any sensitive data to the Clipboard.</span></span>  
  
 <span data-ttu-id="8e7e7-130">`WriteOnly` Modifikátor můžete v tomto kontextu použít:</span><span class="sxs-lookup"><span data-stu-id="8e7e7-130">The `WriteOnly` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="8e7e7-131">Příkaz Property</span><span class="sxs-lookup"><span data-stu-id="8e7e7-131">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="8e7e7-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="8e7e7-132">See Also</span></span>  
 [<span data-ttu-id="8e7e7-133">ReadOnly</span><span class="sxs-lookup"><span data-stu-id="8e7e7-133">ReadOnly</span></span>](../../../visual-basic/language-reference/modifiers/readonly.md)  
 [<span data-ttu-id="8e7e7-134">Private</span><span class="sxs-lookup"><span data-stu-id="8e7e7-134">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
 [<span data-ttu-id="8e7e7-135">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="8e7e7-135">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
