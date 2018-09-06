---
title: Použití aktivity Switch s vlastními typy
ms.date: 03/30/2017
ms.assetid: 482a48c4-eb83-40c3-a4e2-2f9a8af88b75
ms.openlocfilehash: b24a03573b31f3fb1c34d4aa6e03bc11f5b25455
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "44038871"
---
# <a name="usage-of-the-switch-activity-with-custom-types"></a><span data-ttu-id="83359-102">Použití aktivity Switch s vlastními typy</span><span class="sxs-lookup"><span data-stu-id="83359-102">Usage of the Switch Activity with Custom Types</span></span>
<span data-ttu-id="83359-103">Tento příklad popisuje, jak povolit <xref:System.Activities.Statements.Switch%601> aktivity k vyhodnocení, uživatelem definované komplexní typ v době běhu.</span><span class="sxs-lookup"><span data-stu-id="83359-103">This sample describes how to enable a <xref:System.Activities.Statements.Switch%601> activity to evaluate a user-defined complex type at runtime.</span></span> <span data-ttu-id="83359-104">V postupu Většina tradičních programovacích jazycích [přepnout](https://go.microsoft.com/fwlink/?LinkId=180521) příkaz vybere logikou provádění na základě podmíněného vyhodnocení proměnné.</span><span class="sxs-lookup"><span data-stu-id="83359-104">In most traditional procedural programming languages, a [switch](https://go.microsoft.com/fwlink/?LinkId=180521) statement selects an execution logic based on the conditional evaluation of a variable.</span></span> <span data-ttu-id="83359-105">Tradičně `switch` příkaz funguje na výraz, který může být staticky vyhodnocen.</span><span class="sxs-lookup"><span data-stu-id="83359-105">Traditionally, a `switch` statement operates on an expression that can be statically evaluated.</span></span> <span data-ttu-id="83359-106">Například v jazyce C# to znamená, že pouze primitivní typy, jako například <xref:System.Boolean>, <xref:System.Int32>, <xref:System.String>, a jsou podporovány typy výčtu.</span><span class="sxs-lookup"><span data-stu-id="83359-106">For example, in C# this means that only primitive types, such as <xref:System.Boolean>, <xref:System.Int32>, <xref:System.String>, and enumeration types are supported.</span></span>  
  
 <span data-ttu-id="83359-107">Povolit přepínání na vlastní třídu, musí být implementované logiku k vyhodnocení hodnot vlastní komplexního typu za běhu.</span><span class="sxs-lookup"><span data-stu-id="83359-107">To enable switching on a custom class, logic must be implemented to evaluate values of the custom complex type at runtime.</span></span> <span data-ttu-id="83359-108">Tento příklad ukazuje, jak povolit přepínání na vlastní komplexní typ s názvem `Person`.</span><span class="sxs-lookup"><span data-stu-id="83359-108">This sample demonstrates how to enable switching on a custom complex type named `Person`.</span></span>  
  
-   <span data-ttu-id="83359-109">Ve třídě vlastní `Person`, <xref:System.ComponentModel.TypeConverter> je deklarován atribut s názvem vlastní <xref:System.ComponentModel.TypeConverter>.</span><span class="sxs-lookup"><span data-stu-id="83359-109">In the custom class `Person`, a <xref:System.ComponentModel.TypeConverter> attribute is declared with the name of the custom <xref:System.ComponentModel.TypeConverter>.</span></span>  
  
    ```  
    [TypeConverter(typeof(PersonConverter))]  
    public class Person  
    {  
       public string Name { get; set; }  
       public int Age { get; set; }  
    ...  
    ```  
  
-   <span data-ttu-id="83359-110">Ve třídě vlastní `Person`, <xref:System.Object.Equals%2A> a <xref:System.Object.GetHashCode%2A> třídy jsou přepsány.</span><span class="sxs-lookup"><span data-stu-id="83359-110">In the custom class `Person`, the <xref:System.Object.Equals%2A> and <xref:System.Object.GetHashCode%2A> classes are overridden.</span></span>  
  
    ```  
    public override bool Equals(object obj)  
    {  
        Person person = obj as Person;  
  
        if (person != null)  
        {  
            return string.Equals(this.Name, person.Name);  
        }  
  
        return false;  
    }  
  
    public override int GetHashCode()  
    {  
        if (this.Name != null)  
        {  
            return this.Name.GetHashCode();  
        }  
  
        return 0;  
    }  
    ```  
  
-   <span data-ttu-id="83359-111">Vlastní <xref:System.ComponentModel.TypeConverter> třídy je implementováno, který provádí převod instance vlastní třídy na řetězec a řetězec na instanci vlastní třídy.</span><span class="sxs-lookup"><span data-stu-id="83359-111">A custom <xref:System.ComponentModel.TypeConverter> class is implemented that performs the conversion of an instance of the custom class to a string and a string to an instance of a custom class.</span></span>  
  
    ```  
    public class PersonConverter : TypeConverter  
    {  
        public override bool CanConvertFrom(ITypeDescriptorContext context,  
           Type sourceType)  
        {  
            return (sourceType is string);  
        }  
  
        // Overrides the ConvertFrom method of TypeConverter.  
        public override object ConvertFrom(ITypeDescriptorContext context,  
           CultureInfo culture, object value)  
        {  
            if (value == null)  
            {  
                return null;  
            }  
  
            if (value is string)  
            {  
                return new Person  
                {  
                    Name = (string)value  
                };  
            }  
  
            return base.ConvertFrom(context, culture, value);  
        }  
  
        // Overrides the ConvertTo method of TypeConverter.  
        public override object ConvertTo(ITypeDescriptorContext context,  
           CultureInfo culture, object value, Type destinationType)  
        {  
            if (destinationType == typeof(string))  
            {  
                if (value != null)  
                {  
                    return ((Person) value).Name;  
                }  
                else  
                {  
                    return null;  
                }  
            }  
  
            return base.ConvertTo(context, culture, value, destinationType);  
        }  
    }  
    ```  
  
 <span data-ttu-id="83359-112">Následující soubory jsou zahrnuté v této ukázce:</span><span class="sxs-lookup"><span data-stu-id="83359-112">The following files are included in this sample:</span></span>  
  
-   <span data-ttu-id="83359-113">**Person.cs**: definuje `Person` třídy.</span><span class="sxs-lookup"><span data-stu-id="83359-113">**Person.cs**: Defines the `Person` class.</span></span>  
  
-   <span data-ttu-id="83359-114">**PersonConverter.cs**: konvertor typu pro `Person` třídy.</span><span class="sxs-lookup"><span data-stu-id="83359-114">**PersonConverter.cs**: The type converter for the `Person` class.</span></span>  
  
-   <span data-ttu-id="83359-115">**Sequence.XAML**: pracovní postup, který přepne `Person` typu.</span><span class="sxs-lookup"><span data-stu-id="83359-115">**Sequence.xaml**: a workflow that switches over the `Person` type.</span></span>  
  
-   <span data-ttu-id="83359-116">**Soubor program.cs**: hlavní funkci, na kterém běží pracovní postup.</span><span class="sxs-lookup"><span data-stu-id="83359-116">**Program.cs**: The main function that runs the workflow.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="83359-117">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="83359-117">To use this sample</span></span>  
  
1.  <span data-ttu-id="83359-118">Načíst Switch.sln v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="83359-118">Load Switch.sln in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="83359-119">Stiskněte kombinaci kláves CTRL + SHIFT + B, abyste mohli sestavit řešení.</span><span class="sxs-lookup"><span data-stu-id="83359-119">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
3.  <span data-ttu-id="83359-120">Stisknutím CTRL + F5 ke spuštění ukázky.</span><span class="sxs-lookup"><span data-stu-id="83359-120">Press CTRL + F5 to run the sample.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="83359-121">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="83359-121">The samples may already be installed on your machine.</span></span> <span data-ttu-id="83359-122">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="83359-122">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="83359-123">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="83359-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="83359-124">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="83359-124">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\Switch`  
  
## <a name="see-also"></a><span data-ttu-id="83359-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="83359-125">See Also</span></span>  
 [<span data-ttu-id="83359-126">Knihovna předdefinovaných aktivit</span><span class="sxs-lookup"><span data-stu-id="83359-126">Built-In Activity Library</span></span>](../../../../docs/framework/windows-workflow-foundation/net-framework-4-5-built-in-activity-library.md)
