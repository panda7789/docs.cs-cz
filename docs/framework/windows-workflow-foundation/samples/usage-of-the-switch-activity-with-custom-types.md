---
title: "Použití přepínače aktivity s vlastní typy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 482a48c4-eb83-40c3-a4e2-2f9a8af88b75
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2fbf80f0038ad830ab35fdb55272e45d8a6bffdc
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="usage-of-the-switch-activity-with-custom-types"></a>Použití přepínače aktivity s vlastní typy
Tato ukázka popisuje, jak povolit <xref:System.Activities.Statements.Switch%601> aktivity k vyhodnocení, uživatelem definované komplexního typu za běhu. V nejvíce tradiční procedurální programovacích jazyků [přepínač](http://go.microsoft.com/fwlink/?LinkId=180521) příkaz vybere logiky provádění na základě podmíněného vyhodnocení proměnné. Obvyklým `switch` příkaz funguje na výraz, který lze vyhodnotit staticky. Například v jazyce C# to znamená, že pouze primitivní typy, jako například <xref:System.Boolean>, <xref:System.Int32>, <xref:System.String>, a podporované výčtové typy.  
  
 Pokud chcete povolit přepnutí na vlastní třídu, musí být implementované logiku k vyhodnocení hodnot vlastní komplexního typu za běhu. Tento příklad ukazuje, jak povolit přepínání vlastní komplexní typ s názvem `Person`.  
  
-   Ve třídě vlastní `Person`, <xref:System.ComponentModel.TypeConverter> atribut je deklarovaný s názvem vlastní <xref:System.ComponentModel.TypeConverter>.  
  
    ```  
    [TypeConverter(typeof(PersonConverter))]  
    public class Person  
    {  
       public string Name { get; set; }  
       public int Age { get; set; }  
    ...  
    ```  
  
-   Ve třídě vlastní `Person`, <xref:System.Object.Equals%2A> a <xref:System.Object.GetHashCode%2A> jsou přepsaná třídy.  
  
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
  
-   Vlastní <xref:System.ComponentModel.TypeConverter> implementaci třídy, který provede převod instance třídy vlastní řetězec a řetězec na instanci vlastní třídy.  
  
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
  
 Následující soubory jsou zahrnuty v této ukázce:  
  
-   **Person.cs**: definuje `Person` třídy.  
  
-   **PersonConverter.cs**: převaděč typů pro `Person` třídy.  
  
-   **Sequence.XAML**: pracovní postup, který přepne `Person` typu.  
  
-   **Program.cs**: hlavní funkce, která spouští pracovní postup.  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Načíst Switch.sln v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Stisknutím kombinace kláves CTRL + SHIFT + B řešení sestavíte.  
  
3.  Stisknutím kombinace kláves CTRL + F5 ke spuštění ukázky.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\Switch`  
  
## <a name="see-also"></a>Viz také  
 [Knihovna předdefinovaných aktivit](../../../../docs/framework/windows-workflow-foundation/net-framework-4-5-built-in-activity-library.md)
