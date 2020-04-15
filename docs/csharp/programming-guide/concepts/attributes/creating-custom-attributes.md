---
title: Vytváření vlastních atributů (C#)
ms.date: 07/20/2015
ms.assetid: 500e1977-c6de-462d-abce-78a0eb1eda22
ms.openlocfilehash: ec959723c339a13a40fd62388421ceacb736dfca
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389562"
---
# <a name="creating-custom-attributes-c"></a><span data-ttu-id="e8bad-102">Vytváření vlastních atributů (C#)</span><span class="sxs-lookup"><span data-stu-id="e8bad-102">Creating Custom Attributes (C#)</span></span>
<span data-ttu-id="e8bad-103">Vlastní atributy můžete vytvořit definováním třídy atributů, třídy, která <xref:System.Attribute>je přímo nebo nepřímo odvozena z , což umožňuje rychlou a snadnou identifikaci definic atributů v metadatech.</span><span class="sxs-lookup"><span data-stu-id="e8bad-103">You can create your own custom attributes by defining an attribute class, a class that derives directly or indirectly from <xref:System.Attribute>, which makes identifying attribute definitions in metadata fast and easy.</span></span> <span data-ttu-id="e8bad-104">Předpokládejme, že chcete označit typy s názvem programátora, který napsal typ.</span><span class="sxs-lookup"><span data-stu-id="e8bad-104">Suppose you want to tag types with the name of the programmer who wrote the type.</span></span> <span data-ttu-id="e8bad-105">Můžete definovat vlastní `Author` třídu atributů:</span><span class="sxs-lookup"><span data-stu-id="e8bad-105">You might define a custom `Author` attribute class:</span></span>  
  
```csharp  
[System.AttributeUsage(System.AttributeTargets.Class |  
                       System.AttributeTargets.Struct)  
]  
public class Author : System.Attribute  
{  
    private string name;  
    public double version;  
  
    public Author(string name)  
    {  
        this.name = name;  
        version = 1.0;  
    }  
}  
```  
  
 <span data-ttu-id="e8bad-106">Název třídy je název atributu . `Author`</span><span class="sxs-lookup"><span data-stu-id="e8bad-106">The class name is the attribute's name, `Author`.</span></span> <span data-ttu-id="e8bad-107">Je odvozen od `System.Attribute`, takže se jedná o vlastní třídu atributů.</span><span class="sxs-lookup"><span data-stu-id="e8bad-107">It is derived from `System.Attribute`, so it is a custom attribute class.</span></span> <span data-ttu-id="e8bad-108">Parametry konstruktoru jsou poziční parametry vlastního atributu.</span><span class="sxs-lookup"><span data-stu-id="e8bad-108">The constructor's parameters are the custom attribute's positional parameters.</span></span> <span data-ttu-id="e8bad-109">V tomto `name` příkladu je poziční parametr.</span><span class="sxs-lookup"><span data-stu-id="e8bad-109">In this example, `name` is a positional parameter.</span></span> <span data-ttu-id="e8bad-110">Všechna veřejná pole pro čtení a zápis nebo vlastnosti jsou pojmenovány parametry.</span><span class="sxs-lookup"><span data-stu-id="e8bad-110">Any public read-write fields or properties are named parameters.</span></span> <span data-ttu-id="e8bad-111">V tomto `version` případě je pouze pojmenovaný parametr.</span><span class="sxs-lookup"><span data-stu-id="e8bad-111">In this case, `version` is the only named parameter.</span></span> <span data-ttu-id="e8bad-112">Všimněte si `AttributeUsage` použití atributu, aby byl `Author` `struct` atribut platný pouze pro třídu a deklarace.</span><span class="sxs-lookup"><span data-stu-id="e8bad-112">Note the use of the `AttributeUsage` attribute to make the `Author` attribute valid only on class and `struct` declarations.</span></span>  
  
 <span data-ttu-id="e8bad-113">Tento nový atribut můžete použít následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="e8bad-113">You could use this new attribute as follows:</span></span>  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
class SampleClass  
{  
    // P. Ackerman's code goes here...  
}  
```  
  
 <span data-ttu-id="e8bad-114">`AttributeUsage`má pojmenovaný parametr `AllowMultiple`, pomocí kterého můžete vytvořit vlastní atribut na jedno použití nebo vícepoužití.</span><span class="sxs-lookup"><span data-stu-id="e8bad-114">`AttributeUsage` has a named parameter, `AllowMultiple`, with which you can make a custom attribute single-use or multiuse.</span></span> <span data-ttu-id="e8bad-115">V následujícím příkladu kódu je vytvořen víceúčelový atribut.</span><span class="sxs-lookup"><span data-stu-id="e8bad-115">In the following code example, a multiuse attribute is created.</span></span>  
  
```csharp  
[System.AttributeUsage(System.AttributeTargets.Class |  
                       System.AttributeTargets.Struct,  
                       AllowMultiple = true)  // multiuse attribute  
]  
public class Author : System.Attribute  
```  
  
 <span data-ttu-id="e8bad-116">V následujícím příkladu kódu je pro třídu použito více atributů stejného typu.</span><span class="sxs-lookup"><span data-stu-id="e8bad-116">In the following code example, multiple attributes of the same type are applied to a class.</span></span>  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
[Author("R. Koch", version = 1.2)]  
class SampleClass  
{  
    // P. Ackerman's code goes here...  
    // R. Koch's code goes here...  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="e8bad-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="e8bad-117">See also</span></span>

- <xref:System.Reflection>
- [<span data-ttu-id="e8bad-118">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e8bad-118">C# Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="e8bad-119">Zápis vlastních atributů</span><span class="sxs-lookup"><span data-stu-id="e8bad-119">Writing Custom Attributes</span></span>](../../../../standard/attributes/writing-custom-attributes.md)
- [<span data-ttu-id="e8bad-120">Reflexe (C#)</span><span class="sxs-lookup"><span data-stu-id="e8bad-120">Reflection (C#)</span></span>](../reflection.md)
- [<span data-ttu-id="e8bad-121">Atributy (C#)</span><span class="sxs-lookup"><span data-stu-id="e8bad-121">Attributes (C#)</span></span>](./index.md)
- [<span data-ttu-id="e8bad-122">Přístup k atributům pomocí reflexe (C#)</span><span class="sxs-lookup"><span data-stu-id="e8bad-122">Accessing Attributes by Using Reflection (C#)</span></span>](./accessing-attributes-by-using-reflection.md)
- [<span data-ttu-id="e8bad-123">AttributeUsage (C#)</span><span class="sxs-lookup"><span data-stu-id="e8bad-123">AttributeUsage (C#)</span></span>](../../../language-reference/attributes/general.md)
