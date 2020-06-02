---
title: Návrh pole
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- fields, design guidelines
- read-only fields
- member design guidelines, fields
ms.assetid: 7cb4b0f3-7a10-4c93-b84d-733f7134fcf8
ms.openlocfilehash: 3a5ae985ab161899fbb5e96f9b0ef0cfa90b957c
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289743"
---
# <a name="field-design"></a><span data-ttu-id="e7b2d-102">Návrh pole</span><span class="sxs-lookup"><span data-stu-id="e7b2d-102">Field Design</span></span>
<span data-ttu-id="e7b2d-103">Principem zapouzdření je jeden z nejdůležitějších pojmů v objektově orientovaném návrhu.</span><span class="sxs-lookup"><span data-stu-id="e7b2d-103">The principle of encapsulation is one of the most important notions in object-oriented design.</span></span> <span data-ttu-id="e7b2d-104">Tato zásada uvádí, že data uložená v objektu by měla být přístupná pouze k tomuto objektu.</span><span class="sxs-lookup"><span data-stu-id="e7b2d-104">This principle states that data stored inside an object should be accessible only to that object.</span></span>

 <span data-ttu-id="e7b2d-105">Užitečný způsob, jak interpretovat princip, je říci, že by měl být navržen typ tak, aby bylo možné provést změny v polích daného typu (změny názvu nebo typu) bez narušení kódu, který je jiný než pro členy typu.</span><span class="sxs-lookup"><span data-stu-id="e7b2d-105">A useful way to interpret the principle is to say that a type should be designed so that changes to fields of that type (name or type changes) can be made without breaking code other than for members of the type.</span></span> <span data-ttu-id="e7b2d-106">Tato interpretace okamžitě znamená, že všechna pole musí být soukromá.</span><span class="sxs-lookup"><span data-stu-id="e7b2d-106">This interpretation immediately implies that all fields must be private.</span></span>

 <span data-ttu-id="e7b2d-107">Z tohoto striktního omezení vyloučíme pole s konstantním a statickým oprávněním jen pro čtení, protože taková pole, která jsou skoro podle definice, se nikdy nevyžadují ke změně.</span><span class="sxs-lookup"><span data-stu-id="e7b2d-107">We exclude constant and static read-only fields from this strict restriction, because such fields, almost by definition, are never required to change.</span></span>

 <span data-ttu-id="e7b2d-108">❌Neposkytněte pole instance, která jsou veřejná nebo chráněná.</span><span class="sxs-lookup"><span data-stu-id="e7b2d-108">❌ DO NOT provide instance fields that are public or protected.</span></span>

 <span data-ttu-id="e7b2d-109">Měli byste poskytnout vlastnosti pro přístup k polím místo jejich veřejné nebo chráněné.</span><span class="sxs-lookup"><span data-stu-id="e7b2d-109">You should provide properties for accessing fields instead of making them public or protected.</span></span>

 <span data-ttu-id="e7b2d-110">✔️ použít konstantní pole pro konstanty, které se nikdy nezmění.</span><span class="sxs-lookup"><span data-stu-id="e7b2d-110">✔️ DO use constant fields for constants that will never change.</span></span>

 <span data-ttu-id="e7b2d-111">Kompilátor vypálí hodnoty konstantních polí přímo na volání kódu.</span><span class="sxs-lookup"><span data-stu-id="e7b2d-111">The compiler burns the values of const fields directly into calling code.</span></span> <span data-ttu-id="e7b2d-112">Proto hodnoty const nelze nikdy změnit bez rizika přerušení kompatibility.</span><span class="sxs-lookup"><span data-stu-id="e7b2d-112">Therefore, const values can never be changed without the risk of breaking compatibility.</span></span>

 <span data-ttu-id="e7b2d-113">✔️ použít veřejné statické `readonly` pole pro předdefinované instance objektů.</span><span class="sxs-lookup"><span data-stu-id="e7b2d-113">✔️ DO use public static `readonly` fields for predefined object instances.</span></span>

 <span data-ttu-id="e7b2d-114">Pokud existují předdefinované instance typu, deklarujte je jako veřejná pole pouze pro čtení samotného typu.</span><span class="sxs-lookup"><span data-stu-id="e7b2d-114">If there are predefined instances of the type, declare them as public read-only static fields of the type itself.</span></span>

 <span data-ttu-id="e7b2d-115">❌Nepřiřazujte do polí instance proměnlivých typů `readonly` .</span><span class="sxs-lookup"><span data-stu-id="e7b2d-115">❌ DO NOT assign instances of mutable types to `readonly` fields.</span></span>

 <span data-ttu-id="e7b2d-116">Proměnlivý typ je typ s instancemi, které lze změnit po vytvoření instance.</span><span class="sxs-lookup"><span data-stu-id="e7b2d-116">A mutable type is a type with instances that can be modified after they are instantiated.</span></span> <span data-ttu-id="e7b2d-117">Například pole, většina kolekcí a datové proudy jsou proměnlivé typy, ale <xref:System.Int32?displayProperty=nameWithType> , <xref:System.Uri?displayProperty=nameWithType> a <xref:System.String?displayProperty=nameWithType> jsou všechny neměnné.</span><span class="sxs-lookup"><span data-stu-id="e7b2d-117">For example, arrays, most collections, and streams are mutable types, but <xref:System.Int32?displayProperty=nameWithType>, <xref:System.Uri?displayProperty=nameWithType>, and <xref:System.String?displayProperty=nameWithType> are all immutable.</span></span> <span data-ttu-id="e7b2d-118">Modifikátor jen pro čtení v poli typu odkazu brání instanci, která je uložena v poli, aby byla měněna, ale nezabrání v tom, aby byla data instance pole upravována voláním členů, kteří mění instanci.</span><span class="sxs-lookup"><span data-stu-id="e7b2d-118">The read-only modifier on a reference type field prevents the instance stored in the field from being replaced, but it does not prevent the field’s instance data from being modified by calling members changing the instance.</span></span>

 <span data-ttu-id="e7b2d-119">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="e7b2d-119">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="e7b2d-120">*Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*</span><span class="sxs-lookup"><span data-stu-id="e7b2d-120">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="e7b2d-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="e7b2d-121">See also</span></span>

- [<span data-ttu-id="e7b2d-122">Pokyny pro návrh členů</span><span class="sxs-lookup"><span data-stu-id="e7b2d-122">Member Design Guidelines</span></span>](member.md)
- [<span data-ttu-id="e7b2d-123">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="e7b2d-123">Framework Design Guidelines</span></span>](index.md)
