---
title: Pole návrhu
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- fields, design guidelines
- read-only fields
- member design guidelines, fields
ms.assetid: 7cb4b0f3-7a10-4c93-b84d-733f7134fcf8
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2d47934c3fed17f75a97ef5da0397c6ceba53d68
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33571110"
---
# <a name="field-design"></a><span data-ttu-id="a3a76-102">Pole návrhu</span><span class="sxs-lookup"><span data-stu-id="a3a76-102">Field Design</span></span>
<span data-ttu-id="a3a76-103">Princip zapouzdření je jedním z nejdůležitějších pojmy v objektově orientované návrhu.</span><span class="sxs-lookup"><span data-stu-id="a3a76-103">The principle of encapsulation is one of the most important notions in object-oriented design.</span></span> <span data-ttu-id="a3a76-104">Tato zásada se zprávou, že data uložená v objektu by měla být přístupné pouze pro tento objekt.</span><span class="sxs-lookup"><span data-stu-id="a3a76-104">This principle states that data stored inside an object should be accessible only to that object.</span></span>  
  
 <span data-ttu-id="a3a76-105">Užitečný způsob, jak interpretovat princip je to znamená, že by měl být typu navržené tak, aby pole daného typu (název nebo typ změny) můžete měnit, aniž by vás kód jinak než pro členy typu.</span><span class="sxs-lookup"><span data-stu-id="a3a76-105">A useful way to interpret the principle is to say that a type should be designed so that changes to fields of that type (name or type changes) can be made without breaking code other than for members of the type.</span></span> <span data-ttu-id="a3a76-106">Tato interpretace okamžitě znamená, že všechna pole musí být privátní.</span><span class="sxs-lookup"><span data-stu-id="a3a76-106">This interpretation immediately implies that all fields must be private.</span></span>  
  
 <span data-ttu-id="a3a76-107">Konstanty a statické pole jen pro čtení jsme vyloučit z tohoto striktní omezení, protože takové pole, téměř podle definice nikdy musí změnit.</span><span class="sxs-lookup"><span data-stu-id="a3a76-107">We exclude constant and static read-only fields from this strict restriction, because such fields, almost by definition, are never required to change.</span></span>  
  
 <span data-ttu-id="a3a76-108">**X DO NOT** zadejte pole instance, která jsou veřejných nebo chráněný.</span><span class="sxs-lookup"><span data-stu-id="a3a76-108">**X DO NOT** provide instance fields that are public or protected.</span></span>  
  
 <span data-ttu-id="a3a76-109">Pro přístup k pole místo provedení je veřejný nebo chráněného by měl poskytovat vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="a3a76-109">You should provide properties for accessing fields instead of making them public or protected.</span></span>  
  
 <span data-ttu-id="a3a76-110">**✓ DO** pro konstanty, které se budou měnit nikdy používat konstantní pole.</span><span class="sxs-lookup"><span data-stu-id="a3a76-110">**✓ DO** use constant fields for constants that will never change.</span></span>  
  
 <span data-ttu-id="a3a76-111">Kompilátor je nastaven hodnoty polí const přímo do volání kódu.</span><span class="sxs-lookup"><span data-stu-id="a3a76-111">The compiler burns the values of const fields directly into calling code.</span></span> <span data-ttu-id="a3a76-112">Proto const hodnoty nesmí nikdy změnit bez poškození kompatibility.</span><span class="sxs-lookup"><span data-stu-id="a3a76-112">Therefore, const values can never be changed without the risk of breaking compatibility.</span></span>  
  
 <span data-ttu-id="a3a76-113">**✓ DO** použít veřejné statické `readonly` pole pro instance předdefinovaných objektů.</span><span class="sxs-lookup"><span data-stu-id="a3a76-113">**✓ DO** use public static `readonly` fields for predefined object instances.</span></span>  
  
 <span data-ttu-id="a3a76-114">Pokud jsou předdefinované instance typu, deklarujte je jako veřejné jen pro čtení statických polí samotného typu.</span><span class="sxs-lookup"><span data-stu-id="a3a76-114">If there are predefined instances of the type, declare them as public read-only static fields of the type itself.</span></span>  
  
 <span data-ttu-id="a3a76-115">**X DO NOT** přiřadit instancí měnitelný typy `readonly` pole.</span><span class="sxs-lookup"><span data-stu-id="a3a76-115">**X DO NOT** assign instances of mutable types to `readonly` fields.</span></span>  
  
 <span data-ttu-id="a3a76-116">Měnitelný typ je typ s instancí, které můžete změnit, jakmile jsou vytvořeny instance.</span><span class="sxs-lookup"><span data-stu-id="a3a76-116">A mutable type is a type with instances that can be modified after they are instantiated.</span></span> <span data-ttu-id="a3a76-117">Například pole, většina kolekce a datové proudy jsou měnitelný typy, ale <xref:System.Int32?displayProperty=nameWithType>, <xref:System.Uri?displayProperty=nameWithType>, a <xref:System.String?displayProperty=nameWithType> jsou všechny neměnné.</span><span class="sxs-lookup"><span data-stu-id="a3a76-117">For example, arrays, most collections, and streams are mutable types, but <xref:System.Int32?displayProperty=nameWithType>, <xref:System.Uri?displayProperty=nameWithType>, and <xref:System.String?displayProperty=nameWithType> are all immutable.</span></span> <span data-ttu-id="a3a76-118">Modifikátor jen pro čtení na referenční typ pole brání instance uložené v poli od nahrazují, ale nezabrání data instance pole z upravována volání členové změna instance.</span><span class="sxs-lookup"><span data-stu-id="a3a76-118">The read-only modifier on a reference type field prevents the instance stored in the field from being replaced, but it does not prevent the field’s instance data from being modified by calling members changing the instance.</span></span>  
  
 <span data-ttu-id="a3a76-119">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="a3a76-119">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="a3a76-120">*Provedení podle oprávnění Pearson Education, Inc. z [pokynů pro návrh Framework: konvence, Idioms a vzory pro jedno použití knihovny .NET, 2. vydání](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Abrams Brada publikovaná 22 Oct 2008 pomocí Designing Effective jako součást vývoj řady Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="a3a76-120">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3a76-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="a3a76-121">See Also</span></span>  
 [<span data-ttu-id="a3a76-122">Pokyny k návrhu člena</span><span class="sxs-lookup"><span data-stu-id="a3a76-122">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)  
 [<span data-ttu-id="a3a76-123">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="a3a76-123">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
