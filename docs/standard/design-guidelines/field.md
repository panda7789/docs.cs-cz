---
title: Návrh pole
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- fields, design guidelines
- read-only fields
- member design guidelines, fields
ms.assetid: 7cb4b0f3-7a10-4c93-b84d-733f7134fcf8
author: KrzysztofCwalina
ms.openlocfilehash: 3ab8fe279605c4795bb3a26557d0241b186b273a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62026403"
---
# <a name="field-design"></a><span data-ttu-id="02806-102">Návrh pole</span><span class="sxs-lookup"><span data-stu-id="02806-102">Field Design</span></span>
<span data-ttu-id="02806-103">Princip zapouzdření je jedním z nejdůležitějších pojmy v objektově orientovaný návrh.</span><span class="sxs-lookup"><span data-stu-id="02806-103">The principle of encapsulation is one of the most important notions in object-oriented design.</span></span> <span data-ttu-id="02806-104">Tento princip hlásí, že data uložená v objektu by měla být přístupné pouze pro tento objekt.</span><span class="sxs-lookup"><span data-stu-id="02806-104">This principle states that data stored inside an object should be accessible only to that object.</span></span>  
  
 <span data-ttu-id="02806-105">Užitečný způsob, jak interpretovat princip je říct, že typ by měl být navržené tak, aby k polím tohoto typu (název nebo typ změn) můžete změnit bez narušení kód jiný než pro členy typu.</span><span class="sxs-lookup"><span data-stu-id="02806-105">A useful way to interpret the principle is to say that a type should be designed so that changes to fields of that type (name or type changes) can be made without breaking code other than for members of the type.</span></span> <span data-ttu-id="02806-106">Tomto výkladu okamžitě znamená, že všechna pole musí být privátní.</span><span class="sxs-lookup"><span data-stu-id="02806-106">This interpretation immediately implies that all fields must be private.</span></span>  
  
 <span data-ttu-id="02806-107">Vylučujeme konstantní a statické pole jen pro čtení z tohoto striktní omezení, protože pole, podle definice téměř nikdy musejí změnit.</span><span class="sxs-lookup"><span data-stu-id="02806-107">We exclude constant and static read-only fields from this strict restriction, because such fields, almost by definition, are never required to change.</span></span>  
  
 <span data-ttu-id="02806-108">**X DO NOT** zadejte pole instance, která jsou veřejných nebo chráněný.</span><span class="sxs-lookup"><span data-stu-id="02806-108">**X DO NOT** provide instance fields that are public or protected.</span></span>  
  
 <span data-ttu-id="02806-109">Vlastnosti by měla poskytnout pro přístup k pole namísto tak jejich veřejné nebo chráněné.</span><span class="sxs-lookup"><span data-stu-id="02806-109">You should provide properties for accessing fields instead of making them public or protected.</span></span>  
  
 <span data-ttu-id="02806-110">**✓ DO** pro konstanty, které se budou měnit nikdy používat konstantní pole.</span><span class="sxs-lookup"><span data-stu-id="02806-110">**✓ DO** use constant fields for constants that will never change.</span></span>  
  
 <span data-ttu-id="02806-111">Kompilátor se oděl do hodnoty pole const přímo do kódu volání.</span><span class="sxs-lookup"><span data-stu-id="02806-111">The compiler burns the values of const fields directly into calling code.</span></span> <span data-ttu-id="02806-112">Proto konstantních hodnot lze nikdy změnit bez rizika porušení kompatibilitu.</span><span class="sxs-lookup"><span data-stu-id="02806-112">Therefore, const values can never be changed without the risk of breaking compatibility.</span></span>  
  
 <span data-ttu-id="02806-113">**✓ DO** použít veřejné statické `readonly` pole pro instance předdefinovaných objektů.</span><span class="sxs-lookup"><span data-stu-id="02806-113">**✓ DO** use public static `readonly` fields for predefined object instances.</span></span>  
  
 <span data-ttu-id="02806-114">Pokud jsou předdefinované instance daného typu, je deklarujte jako veřejná pole jen pro čtení statické v samotném typu.</span><span class="sxs-lookup"><span data-stu-id="02806-114">If there are predefined instances of the type, declare them as public read-only static fields of the type itself.</span></span>  
  
 <span data-ttu-id="02806-115">**X DO NOT** přiřadit instancí měnitelný typy `readonly` pole.</span><span class="sxs-lookup"><span data-stu-id="02806-115">**X DO NOT** assign instances of mutable types to `readonly` fields.</span></span>  
  
 <span data-ttu-id="02806-116">Měnitelný typ je typ s instancemi, které můžete upravit po jsou vytvořeny.</span><span class="sxs-lookup"><span data-stu-id="02806-116">A mutable type is a type with instances that can be modified after they are instantiated.</span></span> <span data-ttu-id="02806-117">Například pole, většina kolekce a datové proudy jsou měnitelné typy, ale <xref:System.Int32?displayProperty=nameWithType>, <xref:System.Uri?displayProperty=nameWithType>, a <xref:System.String?displayProperty=nameWithType> jsou všechny neměnné.</span><span class="sxs-lookup"><span data-stu-id="02806-117">For example, arrays, most collections, and streams are mutable types, but <xref:System.Int32?displayProperty=nameWithType>, <xref:System.Uri?displayProperty=nameWithType>, and <xref:System.String?displayProperty=nameWithType> are all immutable.</span></span> <span data-ttu-id="02806-118">Modifikátor jen pro čtení na pole typu odkazu brání instance uloženo v poli nahradit, ale nezabrání data instance pole nebylo možné měnit voláním členů změna instance.</span><span class="sxs-lookup"><span data-stu-id="02806-118">The read-only modifier on a reference type field prevents the instance stored in the field from being replaced, but it does not prevent the field’s instance data from being modified by calling members changing the instance.</span></span>  
  
 <span data-ttu-id="02806-119">*Portions © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="02806-119">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="02806-120">*Přetištěno podle oprávnění Pearson vzdělávání, Inc. z [pokyny k návrhu architektury: Konvence, Idiomy a vzory pro opakovaně použitelného knihovny .NET, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Brad Abrams publikován 22 Oct 2008, Designing Effective části této série Microsoft Windows Development.*</span><span class="sxs-lookup"><span data-stu-id="02806-120">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02806-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="02806-121">See also</span></span>

- [<span data-ttu-id="02806-122">Pokyny k návrhu člena</span><span class="sxs-lookup"><span data-stu-id="02806-122">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)
- [<span data-ttu-id="02806-123">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="02806-123">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
