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
ms.openlocfilehash: 43507ac8e9b5843e8fa9496737a3d77b3a425a7f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963773"
---
# <a name="writeonly-visual-basic"></a><span data-ttu-id="5c23e-102">WriteOnly (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5c23e-102">WriteOnly (Visual Basic)</span></span>
<span data-ttu-id="5c23e-103">Určuje, že vlastnost může být zapsána, ale nebude přečtena.</span><span class="sxs-lookup"><span data-stu-id="5c23e-103">Specifies that a property can be written but not read.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5c23e-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5c23e-104">Remarks</span></span>  
  
## <a name="rules"></a><span data-ttu-id="5c23e-105">Pravidly</span><span class="sxs-lookup"><span data-stu-id="5c23e-105">Rules</span></span>  
 <span data-ttu-id="5c23e-106">**Kontext deklarace**</span><span class="sxs-lookup"><span data-stu-id="5c23e-106">**Declaration Context.**</span></span> <span data-ttu-id="5c23e-107">Můžete použít `WriteOnly` pouze na úrovni modulu.</span><span class="sxs-lookup"><span data-stu-id="5c23e-107">You can use `WriteOnly` only at module level.</span></span> <span data-ttu-id="5c23e-108">To znamená, že kontext deklarace pro `WriteOnly` vlastnost musí být třída, struktura nebo modul a nemůže se jednat o zdrojový soubor, obor názvů nebo proceduru.</span><span class="sxs-lookup"><span data-stu-id="5c23e-108">This means the declaration context for a `WriteOnly` property must be a class, structure, or module, and cannot be a source file, namespace, or procedure.</span></span>  
  
 <span data-ttu-id="5c23e-109">Vlastnost můžete deklarovat jako `WriteOnly`, ale ne jako proměnnou.</span><span class="sxs-lookup"><span data-stu-id="5c23e-109">You can declare a property as `WriteOnly`, but not a variable.</span></span>  
  
## <a name="when-to-use-writeonly"></a><span data-ttu-id="5c23e-110">Kdy použít WriteOnly</span><span class="sxs-lookup"><span data-stu-id="5c23e-110">When to Use WriteOnly</span></span>  
 <span data-ttu-id="5c23e-111">Někdy budete chtít, aby kód byl schopný nastavit hodnotu, ale nezjistit, co je.</span><span class="sxs-lookup"><span data-stu-id="5c23e-111">Sometimes you want the consuming code to be able to set a value but not discover what it is.</span></span> <span data-ttu-id="5c23e-112">Například citlivá data, jako je číslo rodného čísla nebo heslo, musí být chráněna před přístupem libovolné součásti, která ji nestavila.</span><span class="sxs-lookup"><span data-stu-id="5c23e-112">For example, sensitive data, such as a social registration number or a password, needs to be protected from access by any component that did not set it.</span></span> <span data-ttu-id="5c23e-113">V těchto případech můžete použít `WriteOnly` vlastnost k nastavení hodnoty.</span><span class="sxs-lookup"><span data-stu-id="5c23e-113">In these cases, you can use a `WriteOnly` property to set the value.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="5c23e-114">Při definování a použití `WriteOnly` vlastnosti Vezměte v úvahu následující dodatečná ochranná opatření:</span><span class="sxs-lookup"><span data-stu-id="5c23e-114">When you define and use a `WriteOnly` property, consider the following additional protective measures:</span></span>  
  
- <span data-ttu-id="5c23e-115">**Přitom.**</span><span class="sxs-lookup"><span data-stu-id="5c23e-115">**Overriding.**</span></span> <span data-ttu-id="5c23e-116">Pokud je vlastnost členem třídy, umožněte jí, aby jí bylo možné [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)a Nedeklarujte ji `Overridable`. `MustOverride`</span><span class="sxs-lookup"><span data-stu-id="5c23e-116">If the property is a member of a class, allow it to default to [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md), and do not declare it `Overridable` or `MustOverride`.</span></span> <span data-ttu-id="5c23e-117">Tím zabráníte odvozeným třídám v provedení nežádoucího přístupu prostřednictvím přepsání.</span><span class="sxs-lookup"><span data-stu-id="5c23e-117">This prevents a derived class from making undesired access through an override.</span></span>  
  
- <span data-ttu-id="5c23e-118">**Úroveň přístupu.**</span><span class="sxs-lookup"><span data-stu-id="5c23e-118">**Access Level.**</span></span> <span data-ttu-id="5c23e-119">Pokud podržíte citlivá data vlastnosti v jedné nebo více proměnných, deklarujte je jako [soukromá](../../../visual-basic/language-reference/modifiers/private.md) , aby k nim nikdo nepřístupoval žádný jiný kód.</span><span class="sxs-lookup"><span data-stu-id="5c23e-119">If you hold the property's sensitive data in one or more variables, declare them [Private](../../../visual-basic/language-reference/modifiers/private.md) so that no other code can access them.</span></span>  
  
- <span data-ttu-id="5c23e-120">**Šifr.**</span><span class="sxs-lookup"><span data-stu-id="5c23e-120">**Encryption.**</span></span> <span data-ttu-id="5c23e-121">Ukládat všechna citlivá data v zašifrované podobě, nikoli v prostém textu.</span><span class="sxs-lookup"><span data-stu-id="5c23e-121">Store all sensitive data in encrypted form rather than in plain text.</span></span> <span data-ttu-id="5c23e-122">Pokud škodlivý kód nějakým způsobem získá přístup k této oblasti paměti, je obtížnější využít data.</span><span class="sxs-lookup"><span data-stu-id="5c23e-122">If malicious code somehow gains access to that area of memory, it is more difficult to make use of the data.</span></span> <span data-ttu-id="5c23e-123">Šifrování je užitečné také v případě, že je nutné serializovat citlivá data.</span><span class="sxs-lookup"><span data-stu-id="5c23e-123">Encryption is also useful if it is necessary to serialize the sensitive data.</span></span>  
  
- <span data-ttu-id="5c23e-124">**Resetování.**</span><span class="sxs-lookup"><span data-stu-id="5c23e-124">**Resetting.**</span></span> <span data-ttu-id="5c23e-125">Když je ukončena třída, struktura nebo modul definující vlastnost, resetujte citlivé údaje na výchozí hodnoty nebo jiné nevýznamné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="5c23e-125">When the class, structure, or module defining the property is being terminated, reset the sensitive data to default values or to other meaningless values.</span></span> <span data-ttu-id="5c23e-126">To poskytuje dodatečnou ochranu, pokud je tato oblast paměti uvolněna pro obecný přístup.</span><span class="sxs-lookup"><span data-stu-id="5c23e-126">This gives extra protection when that area of memory is freed for general access.</span></span>  
  
- <span data-ttu-id="5c23e-127">**Dočasné.**</span><span class="sxs-lookup"><span data-stu-id="5c23e-127">**Persistence.**</span></span> <span data-ttu-id="5c23e-128">Neuchovávat žádná citlivá data, například na disku, pokud se k tomu můžete vyhnout.</span><span class="sxs-lookup"><span data-stu-id="5c23e-128">Do not persist any sensitive data, for example on disk, if you can avoid it.</span></span> <span data-ttu-id="5c23e-129">Nepište také žádná citlivá data do schránky.</span><span class="sxs-lookup"><span data-stu-id="5c23e-129">Also, do not write any sensitive data to the Clipboard.</span></span>  
  
 <span data-ttu-id="5c23e-130">V tomto kontextu lze použít Modifikátor:`WriteOnly`</span><span class="sxs-lookup"><span data-stu-id="5c23e-130">The `WriteOnly` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="5c23e-131">Příkaz Property</span><span class="sxs-lookup"><span data-stu-id="5c23e-131">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="5c23e-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5c23e-132">See also</span></span>

- [<span data-ttu-id="5c23e-133">ReadOnly</span><span class="sxs-lookup"><span data-stu-id="5c23e-133">ReadOnly</span></span>](../../../visual-basic/language-reference/modifiers/readonly.md)
- [<span data-ttu-id="5c23e-134">Private</span><span class="sxs-lookup"><span data-stu-id="5c23e-134">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)
- [<span data-ttu-id="5c23e-135">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="5c23e-135">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
