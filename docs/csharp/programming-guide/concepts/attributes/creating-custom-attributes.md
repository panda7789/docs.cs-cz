---
title: Vytváření vlastních atributů (C#)
description: Naučte se vytvářet vlastní atributy v jazyce C# definováním třídy atributů, která je odvozena od třídy atributů.
ms.date: 07/20/2015
ms.assetid: 500e1977-c6de-462d-abce-78a0eb1eda22
ms.openlocfilehash: 7d6f98620388af8715652dcbcfe78366952b853d
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925082"
---
# <a name="creating-custom-attributes-c"></a><span data-ttu-id="daf34-103">Vytváření vlastních atributů (C#)</span><span class="sxs-lookup"><span data-stu-id="daf34-103">Creating Custom Attributes (C#)</span></span>
<span data-ttu-id="daf34-104">Můžete vytvořit vlastní atributy definováním třídy atributů, třídy, která je odvozena přímo nebo nepřímo z <xref:System.Attribute> , což umožňuje rychlou a jednoduchou identifikaci definic atributů v metadatech.</span><span class="sxs-lookup"><span data-stu-id="daf34-104">You can create your own custom attributes by defining an attribute class, a class that derives directly or indirectly from <xref:System.Attribute>, which makes identifying attribute definitions in metadata fast and easy.</span></span> <span data-ttu-id="daf34-105">Předpokládejme, že chcete označit typy s názvem programátora, který typ napsal.</span><span class="sxs-lookup"><span data-stu-id="daf34-105">Suppose you want to tag types with the name of the programmer who wrote the type.</span></span> <span data-ttu-id="daf34-106">Je možné definovat vlastní `Author` třídu atributu:</span><span class="sxs-lookup"><span data-stu-id="daf34-106">You might define a custom `Author` attribute class:</span></span>  
  
```csharp  
[System.AttributeUsage(System.AttributeTargets.Class |  
                       System.AttributeTargets.Struct)  
]  
public class AuthorAttribute : System.Attribute  
{  
    private string name;  
    public double version;  
  
    public AuthorAttribute(string name)  
    {  
        this.name = name;  
        version = 1.0;  
    }  
}  
```  
  
 <span data-ttu-id="daf34-107">Název třídy `AuthorAttribute` je název atributu, `Author` a navíc `Attribute` přípona.</span><span class="sxs-lookup"><span data-stu-id="daf34-107">The class name `AuthorAttribute` is the attribute's name, `Author`, plus the `Attribute` suffix.</span></span> <span data-ttu-id="daf34-108">Je odvozen z `System.Attribute` , takže se jedná o vlastní třídu atributu.</span><span class="sxs-lookup"><span data-stu-id="daf34-108">It is derived from `System.Attribute`, so it is a custom attribute class.</span></span> <span data-ttu-id="daf34-109">Parametry konstruktoru jsou poziční parametry vlastního atributu.</span><span class="sxs-lookup"><span data-stu-id="daf34-109">The constructor's parameters are the custom attribute's positional parameters.</span></span> <span data-ttu-id="daf34-110">V tomto příkladu `name` je poziční parametr.</span><span class="sxs-lookup"><span data-stu-id="daf34-110">In this example, `name` is a positional parameter.</span></span> <span data-ttu-id="daf34-111">Všechna veřejná pole nebo vlastnosti pro čtení i zápis se nazývají parametry.</span><span class="sxs-lookup"><span data-stu-id="daf34-111">Any public read-write fields or properties are named parameters.</span></span> <span data-ttu-id="daf34-112">V tomto případě `version` je jediným pojmenovaným parametrem.</span><span class="sxs-lookup"><span data-stu-id="daf34-112">In this case, `version` is the only named parameter.</span></span> <span data-ttu-id="daf34-113">Všimněte si, že použití `AttributeUsage` atributu pro nastavení `Author` atributu je platné pouze pro třídu a `struct` deklarace.</span><span class="sxs-lookup"><span data-stu-id="daf34-113">Note the use of the `AttributeUsage` attribute to make the `Author` attribute valid only on class and `struct` declarations.</span></span>  
  
 <span data-ttu-id="daf34-114">Tento nový atribut můžete použít následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="daf34-114">You could use this new attribute as follows:</span></span>  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
class SampleClass  
{  
    // P. Ackerman's code goes here...  
}  
```  
  
 <span data-ttu-id="daf34-115">`AttributeUsage`má pojmenovaný parametr, `AllowMultiple` pomocí kterého můžete vytvořit vlastní atribut s jedním použitím nebo Multiuse.</span><span class="sxs-lookup"><span data-stu-id="daf34-115">`AttributeUsage` has a named parameter, `AllowMultiple`, with which you can make a custom attribute single-use or multiuse.</span></span> <span data-ttu-id="daf34-116">V následujícím příkladu kódu je vytvořen atribut Multiuse.</span><span class="sxs-lookup"><span data-stu-id="daf34-116">In the following code example, a multiuse attribute is created.</span></span>  
  
```csharp  
[System.AttributeUsage(System.AttributeTargets.Class |  
                       System.AttributeTargets.Struct,  
                       AllowMultiple = true)  // multiuse attribute  
]  
public class AuthorAttribute : System.Attribute  
```  
  
 <span data-ttu-id="daf34-117">V následujícím příkladu kódu je pro třídu použito více atributů stejného typu.</span><span class="sxs-lookup"><span data-stu-id="daf34-117">In the following code example, multiple attributes of the same type are applied to a class.</span></span>  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
[Author("R. Koch", version = 1.2)]  
class SampleClass  
{  
    // P. Ackerman's code goes here...  
    // R. Koch's code goes here...  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="daf34-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="daf34-118">See also</span></span>

- <xref:System.Reflection>
- [<span data-ttu-id="daf34-119">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="daf34-119">C# Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="daf34-120">Zápis vlastních atributů</span><span class="sxs-lookup"><span data-stu-id="daf34-120">Writing Custom Attributes</span></span>](../../../../standard/attributes/writing-custom-attributes.md)
- [<span data-ttu-id="daf34-121">Reflexe (C#)</span><span class="sxs-lookup"><span data-stu-id="daf34-121">Reflection (C#)</span></span>](../reflection.md)
- [<span data-ttu-id="daf34-122">Atributy (C#)</span><span class="sxs-lookup"><span data-stu-id="daf34-122">Attributes (C#)</span></span>](./index.md)
- [<span data-ttu-id="daf34-123">Přístup k atributům pomocí reflexe (C#)</span><span class="sxs-lookup"><span data-stu-id="daf34-123">Accessing Attributes by Using Reflection (C#)</span></span>](./accessing-attributes-by-using-reflection.md)
- [<span data-ttu-id="daf34-124">AttributeUsage (C#)</span><span class="sxs-lookup"><span data-stu-id="daf34-124">AttributeUsage (C#)</span></span>](../../../language-reference/attributes/general.md)
