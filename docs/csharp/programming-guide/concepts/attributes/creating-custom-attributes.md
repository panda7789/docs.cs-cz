---
title: Vytváření vlastních atributů (C#)
ms.date: 07/20/2015
ms.assetid: 500e1977-c6de-462d-abce-78a0eb1eda22
ms.openlocfilehash: c0f25adf0d562b659edaa8f36e72332fd0c1ee7e
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595415"
---
# <a name="creating-custom-attributes-c"></a><span data-ttu-id="02519-102">Vytváření vlastních atributů (C#)</span><span class="sxs-lookup"><span data-stu-id="02519-102">Creating Custom Attributes (C#)</span></span>
<span data-ttu-id="02519-103">Můžete vytvořit vlastní atributy definováním třídy atributů, třídy, která je odvozena přímo nebo nepřímo z <xref:System.Attribute>, což umožňuje rychlou a jednoduchou identifikaci definic atributů v metadatech.</span><span class="sxs-lookup"><span data-stu-id="02519-103">You can create your own custom attributes by defining an attribute class, a class that derives directly or indirectly from <xref:System.Attribute>, which makes identifying attribute definitions in metadata fast and easy.</span></span> <span data-ttu-id="02519-104">Předpokládejme, že chcete označit typy s názvem programátora, který typ napsal.</span><span class="sxs-lookup"><span data-stu-id="02519-104">Suppose you want to tag types with the name of the programmer who wrote the type.</span></span> <span data-ttu-id="02519-105">Je možné definovat vlastní `Author` třídu atributu:</span><span class="sxs-lookup"><span data-stu-id="02519-105">You might define a custom `Author` attribute class:</span></span>  
  
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
  
 <span data-ttu-id="02519-106">Název třídy je název atributu, `Author`.</span><span class="sxs-lookup"><span data-stu-id="02519-106">The class name is the attribute's name, `Author`.</span></span> <span data-ttu-id="02519-107">Je odvozen z `System.Attribute`, takže se jedná o vlastní třídu atributu.</span><span class="sxs-lookup"><span data-stu-id="02519-107">It is derived from `System.Attribute`, so it is a custom attribute class.</span></span> <span data-ttu-id="02519-108">Parametry konstruktoru jsou poziční parametry vlastního atributu.</span><span class="sxs-lookup"><span data-stu-id="02519-108">The constructor's parameters are the custom attribute's positional parameters.</span></span> <span data-ttu-id="02519-109">V tomto příkladu `name` je poziční parametr.</span><span class="sxs-lookup"><span data-stu-id="02519-109">In this example, `name` is a positional parameter.</span></span> <span data-ttu-id="02519-110">Všechna veřejná pole nebo vlastnosti pro čtení i zápis se nazývají parametry.</span><span class="sxs-lookup"><span data-stu-id="02519-110">Any public read-write fields or properties are named parameters.</span></span> <span data-ttu-id="02519-111">V tomto případě `version` je jediným pojmenovaným parametrem.</span><span class="sxs-lookup"><span data-stu-id="02519-111">In this case, `version` is the only named parameter.</span></span> <span data-ttu-id="02519-112">Všimněte si, že použití `AttributeUsage` atributu pro nastavení atributu `Author` je platné pouze pro třídu a `struct` deklarace.</span><span class="sxs-lookup"><span data-stu-id="02519-112">Note the use of the `AttributeUsage` attribute to make the `Author` attribute valid only on class and `struct` declarations.</span></span>  
  
 <span data-ttu-id="02519-113">Tento nový atribut můžete použít následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="02519-113">You could use this new attribute as follows:</span></span>  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
class SampleClass  
{  
    // P. Ackerman's code goes here...  
}  
```  
  
 <span data-ttu-id="02519-114">`AttributeUsage`má pojmenovaný parametr, `AllowMultiple`pomocí kterého můžete vytvořit vlastní atribut s jedním použitím nebo Multiuse.</span><span class="sxs-lookup"><span data-stu-id="02519-114">`AttributeUsage` has a named parameter, `AllowMultiple`, with which you can make a custom attribute single-use or multiuse.</span></span> <span data-ttu-id="02519-115">V následujícím příkladu kódu je vytvořen atribut Multiuse.</span><span class="sxs-lookup"><span data-stu-id="02519-115">In the following code example, a multiuse attribute is created.</span></span>  
  
```csharp  
[System.AttributeUsage(System.AttributeTargets.Class |  
                       System.AttributeTargets.Struct,  
                       AllowMultiple = true)  // multiuse attribute  
]  
public class Author : System.Attribute  
```  
  
 <span data-ttu-id="02519-116">V následujícím příkladu kódu je pro třídu použito více atributů stejného typu.</span><span class="sxs-lookup"><span data-stu-id="02519-116">In the following code example, multiple attributes of the same type are applied to a class.</span></span>  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
[Author("R. Koch", version = 1.2)]  
class SampleClass  
{  
    // P. Ackerman's code goes here...  
    // R. Koch's code goes here...  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="02519-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="02519-117">See also</span></span>

- <xref:System.Reflection>
- [<span data-ttu-id="02519-118">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="02519-118">C# Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="02519-119">Zápis vlastních atributů</span><span class="sxs-lookup"><span data-stu-id="02519-119">Writing Custom Attributes</span></span>](../../../../standard/attributes/writing-custom-attributes.md)
- [<span data-ttu-id="02519-120">Reflexe (C#)</span><span class="sxs-lookup"><span data-stu-id="02519-120">Reflection (C#)</span></span>](../reflection.md)
- [<span data-ttu-id="02519-121">Atributy (C#)</span><span class="sxs-lookup"><span data-stu-id="02519-121">Attributes (C#)</span></span>](./index.md)
- [<span data-ttu-id="02519-122">Přístup k atributům pomocí reflexe (C#)</span><span class="sxs-lookup"><span data-stu-id="02519-122">Accessing Attributes by Using Reflection (C#)</span></span>](./accessing-attributes-by-using-reflection.md)
- [<span data-ttu-id="02519-123">AttributeUsage (C#)</span><span class="sxs-lookup"><span data-stu-id="02519-123">AttributeUsage (C#)</span></span>](./attributeusage.md)
