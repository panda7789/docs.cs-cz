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
ms.openlocfilehash: 1b8de27e872914ba59d73126d2a9a7c42609165e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62051816"
---
# <a name="writeonly-visual-basic"></a><span data-ttu-id="1acee-102">WriteOnly (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1acee-102">WriteOnly (Visual Basic)</span></span>
<span data-ttu-id="1acee-103">Určuje, že vlastnost může zapisovat, ale nedá se číst.</span><span class="sxs-lookup"><span data-stu-id="1acee-103">Specifies that a property can be written but not read.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1acee-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1acee-104">Remarks</span></span>  
  
## <a name="rules"></a><span data-ttu-id="1acee-105">pravidla</span><span class="sxs-lookup"><span data-stu-id="1acee-105">Rules</span></span>  
 <span data-ttu-id="1acee-106">**Místní deklarace.**</span><span class="sxs-lookup"><span data-stu-id="1acee-106">**Declaration Context.**</span></span> <span data-ttu-id="1acee-107">Můžete použít `WriteOnly` pouze na úrovni modulu.</span><span class="sxs-lookup"><span data-stu-id="1acee-107">You can use `WriteOnly` only at module level.</span></span> <span data-ttu-id="1acee-108">To znamená, že deklarace kontext `WriteOnly` vlastnost musí být třída, struktura nebo modulu a nemůže být zdrojový soubor, obor názvů nebo proceduru.</span><span class="sxs-lookup"><span data-stu-id="1acee-108">This means the declaration context for a `WriteOnly` property must be a class, structure, or module, and cannot be a source file, namespace, or procedure.</span></span>  
  
 <span data-ttu-id="1acee-109">Je možné deklarovat vlastnost jako `WriteOnly`, ale není proměnná.</span><span class="sxs-lookup"><span data-stu-id="1acee-109">You can declare a property as `WriteOnly`, but not a variable.</span></span>  
  
## <a name="when-to-use-writeonly"></a><span data-ttu-id="1acee-110">Kdy použít jen pro zápis</span><span class="sxs-lookup"><span data-stu-id="1acee-110">When to Use WriteOnly</span></span>  
 <span data-ttu-id="1acee-111">Někdy chcete být schopni nastavit hodnotu, ale ne zjistit, co to je časově náročný kód.</span><span class="sxs-lookup"><span data-stu-id="1acee-111">Sometimes you want the consuming code to be able to set a value but not discover what it is.</span></span> <span data-ttu-id="1acee-112">Například citlivá data, jako jsou sociální registrační číslo nebo heslo, musí být chráněny před přístup jakékoli součásti, která nebyla nastavena.</span><span class="sxs-lookup"><span data-stu-id="1acee-112">For example, sensitive data, such as a social registration number or a password, needs to be protected from access by any component that did not set it.</span></span> <span data-ttu-id="1acee-113">V těchto případech můžete použít `WriteOnly` vlastnosti chcete nastavit hodnotu.</span><span class="sxs-lookup"><span data-stu-id="1acee-113">In these cases, you can use a `WriteOnly` property to set the value.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="1acee-114">Při definování a použití `WriteOnly` vlastnost, vezměte v úvahu následující další ochranná opatření:</span><span class="sxs-lookup"><span data-stu-id="1acee-114">When you define and use a `WriteOnly` property, consider the following additional protective measures:</span></span>  
  
- <span data-ttu-id="1acee-115">**Přepsání.**</span><span class="sxs-lookup"><span data-stu-id="1acee-115">**Overriding.**</span></span> <span data-ttu-id="1acee-116">Pokud je vlastnost člena třídy, mohla ve výchozím nastavení [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)a ne jeho deklarace `Overridable` nebo `MustOverride`.</span><span class="sxs-lookup"><span data-stu-id="1acee-116">If the property is a member of a class, allow it to default to [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md), and do not declare it `Overridable` or `MustOverride`.</span></span> <span data-ttu-id="1acee-117">To brání odvozené třídy v provádění nežádoucích přístup pomocí přepsání.</span><span class="sxs-lookup"><span data-stu-id="1acee-117">This prevents a derived class from making undesired access through an override.</span></span>  
  
- <span data-ttu-id="1acee-118">**Úroveň přístupu.**</span><span class="sxs-lookup"><span data-stu-id="1acee-118">**Access Level.**</span></span> <span data-ttu-id="1acee-119">Pokud jste v jedné nebo více proměnných citlivých dat vlastnost, je deklarovat [privátní](../../../visual-basic/language-reference/modifiers/private.md) tak, aby k nim může přistupovat žádný kód.</span><span class="sxs-lookup"><span data-stu-id="1acee-119">If you hold the property's sensitive data in one or more variables, declare them [Private](../../../visual-basic/language-reference/modifiers/private.md) so that no other code can access them.</span></span>  
  
- <span data-ttu-id="1acee-120">**Šifrování.**</span><span class="sxs-lookup"><span data-stu-id="1acee-120">**Encryption.**</span></span> <span data-ttu-id="1acee-121">Store všechna citlivá data v zašifrované podobě, nikoli ve formátu prostého textu.</span><span class="sxs-lookup"><span data-stu-id="1acee-121">Store all sensitive data in encrypted form rather than in plain text.</span></span> <span data-ttu-id="1acee-122">Pokud škodlivý kód nějakým způsobem získá přístup k této oblasti paměti, je obtížnější, chcete-li využívají data.</span><span class="sxs-lookup"><span data-stu-id="1acee-122">If malicious code somehow gains access to that area of memory, it is more difficult to make use of the data.</span></span> <span data-ttu-id="1acee-123">Šifrování je také užitečné, pokud je nutné k serializaci citlivá data.</span><span class="sxs-lookup"><span data-stu-id="1acee-123">Encryption is also useful if it is necessary to serialize the sensitive data.</span></span>  
  
- <span data-ttu-id="1acee-124">**Resetuje se.**</span><span class="sxs-lookup"><span data-stu-id="1acee-124">**Resetting.**</span></span> <span data-ttu-id="1acee-125">Když se ukončuje třídy, struktury nebo modul definující vlastnosti, obnovit citlivých dat na výchozí hodnoty nebo na další význam hodnoty.</span><span class="sxs-lookup"><span data-stu-id="1acee-125">When the class, structure, or module defining the property is being terminated, reset the sensitive data to default values or to other meaningless values.</span></span> <span data-ttu-id="1acee-126">Díky tomu ochrany při této oblasti paměti je uvolněna obecného přístupu.</span><span class="sxs-lookup"><span data-stu-id="1acee-126">This gives extra protection when that area of memory is freed for general access.</span></span>  
  
- <span data-ttu-id="1acee-127">**Trvalost.**</span><span class="sxs-lookup"><span data-stu-id="1acee-127">**Persistence.**</span></span> <span data-ttu-id="1acee-128">Pokud ho se můžete vyhnout nezůstanou zachována citlivých dat, třeba na disku.</span><span class="sxs-lookup"><span data-stu-id="1acee-128">Do not persist any sensitive data, for example on disk, if you can avoid it.</span></span> <span data-ttu-id="1acee-129">Citlivé údaje taky nezapisujte do schránky.</span><span class="sxs-lookup"><span data-stu-id="1acee-129">Also, do not write any sensitive data to the Clipboard.</span></span>  
  
 <span data-ttu-id="1acee-130">`WriteOnly` Modifikátor lze použít v tomto kontextu:</span><span class="sxs-lookup"><span data-stu-id="1acee-130">The `WriteOnly` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="1acee-131">Příkaz Property</span><span class="sxs-lookup"><span data-stu-id="1acee-131">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="1acee-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1acee-132">See also</span></span>

- [<span data-ttu-id="1acee-133">ReadOnly</span><span class="sxs-lookup"><span data-stu-id="1acee-133">ReadOnly</span></span>](../../../visual-basic/language-reference/modifiers/readonly.md)
- [<span data-ttu-id="1acee-134">Private</span><span class="sxs-lookup"><span data-stu-id="1acee-134">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)
- [<span data-ttu-id="1acee-135">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="1acee-135">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
