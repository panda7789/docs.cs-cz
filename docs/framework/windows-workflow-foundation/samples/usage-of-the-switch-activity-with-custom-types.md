---
title: Použití aktivity Switch s vlastními typy
ms.date: 03/30/2017
ms.assetid: 482a48c4-eb83-40c3-a4e2-2f9a8af88b75
ms.openlocfilehash: b24a03573b31f3fb1c34d4aa6e03bc11f5b25455
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43535436"
---
# <a name="usage-of-the-switch-activity-with-custom-types"></a>Použití aktivity Switch s vlastními typy
Tento příklad popisuje, jak povolit <xref:System.Activities.Statements.Switch%601> aktivity k vyhodnocení, uživatelem definované komplexní typ v době běhu. V postupu Většina tradičních programovacích jazycích [přepnout](https://go.microsoft.com/fwlink/?LinkId=180521) příkaz vybere logikou provádění na základě podmíněného vyhodnocení proměnné. Tradičně `switch` příkaz funguje na výraz, který může být staticky vyhodnocen. Například v jazyce C# to znamená, že pouze primitivní typy, jako například <xref:System.Boolean>, <xref:System.Int32>, <xref:System.String>, a jsou podporovány typy výčtu.  
  
 Povolit přepínání na vlastní třídu, musí být implementované logiku k vyhodnocení hodnot vlastní komplexního typu za běhu. Tento příklad ukazuje, jak povolit přepínání na vlastní komplexní typ s názvem `Person`.  
  
-   Ve třídě vlastní `Person`, <xref:System.ComponentModel.TypeConverter> je deklarován atribut s názvem vlastní <xref:System.ComponentModel.TypeConverter>.  
  
    ```  
    [TypeConverter(typeof(PersonConverter))]  
    public class Person  
    {  
       public string Name { get; set; }  
       public int Age { get; set; }  
    ...  
    ```  
  
-   Ve třídě vlastní `Person`, <xref:System.Object.Equals%2A> a <xref:System.Object.GetHashCode%2A> třídy jsou přepsány.  
  
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
  
-   Vlastní <xref:System.ComponentModel.TypeConverter> třídy je implementováno, který provádí převod instance vlastní třídy na řetězec a řetězec na instanci vlastní třídy.  
  
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
  
 Následující soubory jsou zahrnuté v této ukázce:  
  
-   **Person.cs**: definuje `Person` třídy.  
  
-   **PersonConverter.cs**: konvertor typu pro `Person` třídy.  
  
-   **Sequence.XAML**: pracovní postup, který přepne `Person` typu.  
  
-   **Soubor program.cs**: hlavní funkci, na kterém běží pracovní postup.  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Načíst Switch.sln v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Stiskněte kombinaci kláves CTRL + SHIFT + B, abyste mohli sestavit řešení.  
  
3.  Stisknutím CTRL + F5 ke spuštění ukázky.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\Switch`  
  
## <a name="see-also"></a>Viz také  
 [Knihovna předdefinovaných aktivit](../../../../docs/framework/windows-workflow-foundation/net-framework-4-5-built-in-activity-library.md)
