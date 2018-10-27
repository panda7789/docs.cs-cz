---
title: Povinné argumenty a skupiny přetížení
ms.date: 03/30/2017
ms.assetid: 4ca3ed06-b9af-4b85-8b70-88c2186aefa3
ms.openlocfilehash: d7cfe00d93f1eede77bcda5881c63843722c9a17
ms.sourcegitcommit: b22705f1540b237c566721018f974822d5cd8758
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2018
ms.locfileid: "49452898"
---
# <a name="required-arguments-and-overload-groups"></a>Povinné argumenty a skupiny přetížení
Aktivity lze nastavit tak, aby některé argumenty jsou povinné vázat pro aktivitu platná pro spuštění. `RequiredArgument` Atribut se používá k označení, že se vyžadují některé argumenty pro aktivitu a `OverloadGroup` atribut se používá k seskupení kategorie povinnými argumenty. Pomocí atributů lze aktivity autoři uvádějí aktivitu jednoduchých nebo složitých ověření konfigurace.  
  
## <a name="using-required-arguments"></a>Povinné argumenty  
 Použít `RequiredArgument` atribut v aktivitě, označení požadovaného argumentů pomocí <xref:System.Activities.RequiredArgumentAttribute>. V tomto příkladu `Add` aktivity je definován, že má dvě povinné argumenty.  
  
```csharp  
public sealed class Add : CodeActivity<int>  
{  
    [RequiredArgument]  
    public InArgument<int> Operand1 { get; set; }  
  
    [RequiredArgument]  
    public InArgument<int> Operand2 { get; set; }  
  
    protected override int Execute(CodeActivityContext context)  
    {  
        return Operand1.Get(context) + Operand2.Get(context);  
    }  
}  
```  
  
 V XAML, povinnými argumenty jsou také uvedeny pomocí <xref:System.Activities.RequiredArgumentAttribute>. V tomto příkladu `Add` aktivity je definován pomocí tří argumentů a použije <xref:System.Activities.Statements.Assign%601> aktivita k provedení operace přidání.  
  
```xaml  
<Activity x:Class="ValidationDemo.Add" ...>  
  <x:Members>  
    <x:Property Name="Operand1" Type="InArgument(x:Int32)">  
      <x:Property.Attributes>  
        <RequiredArgumentAttribute />  
      </x:Property.Attributes>  
    </x:Property>  
    <x:Property Name="Operand2" Type="InArgument(x:Int32)">  
      <x:Property.Attributes>  
        <RequiredArgumentAttribute />  
      </x:Property.Attributes>  
    </x:Property>  
    <x:Property Name="Result" Type="OutArgument(x:Int32)" />  
  </x:Members>  
  <Assign>  
    <Assign.To>  
      <OutArgument x:TypeArguments="x:Int32">[Result]</OutArgument>  
    </Assign.To>  
    <Assign.Value>  
      <InArgument x:TypeArguments="x:Int32">[Operand1 + Operand2]</InArgument>  
    </Assign.Value>  
  </Assign>  
</Activity>  
```  
  
 Pokud se používá aktivitu a není vázaná buď povinnými argumenty vrátil následující chybu ověření.  
  
 **Nebyla zadána hodnota pro povinný argument aktivity "Operand1".**  
> [!NOTE]
> Další informace o zjišťování a zpracování chyby a upozornění ověření najdete v tématu [vyvolání ověřování aktivit](../../../docs/framework/windows-workflow-foundation/invoking-activity-validation.md).  
  
## <a name="using-overload-groups"></a>Používání skupiny přetížení

Přetížené skupiny poskytují metoda označující, jaké kombinace argumentů jsou platné v nějaké aktivitě. Argumenty jsou seskupené dohromady pomocí <xref:System.Activities.OverloadGroupAttribute>. Každá skupina je přiřazen název, který je určen <xref:System.Activities.OverloadGroupAttribute>. Aktivita je platný, pokud jsou svázány pouze jednu sadu argumentů v přetížené skupině. V následujícím příkladu `CreateLocation` třída je definována.  
  
```csharp  
class CreateLocation: Activity  
{  
    [RequiredArgument]  
    public InArgument<string> Name { get; set; }  
  
    public InArgument<string> Description { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("G1")]  
    public InArgument<int> Latitude { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("G1")]  
    public InArgument<int> Longitude { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("G2")]  
    [OverloadGroup("G3")]  
    public InArgument<string> Street { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("G2")]  
    public InArgument<string> City { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("G2")]  
    public InArgument<string> State { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("G3")]  
    public InArgument<int> Zip { get; set; }                  
}  
```  
  
 Cílem této aktivity je a zadejte umístění v USA. K tomuto účelu můžete zadat uživatelské aktivity umístění pomocí jedné ze tří skupin argumentů. Chcete-li určit platné kombinace argumentů, jsou definovány tři přetížené skupiny. `G1` obsahuje `Latitude` a `Longitude` argumenty. `G2` obsahuje `Street`, `City`, a `State`. `G3` obsahuje `Street` a `Zip`. `Name` je také požadovaný argument, ale není součástí skupiny přetížení. Pro tuto aktivitu platná `Name` musel být vázaný spolu s všechny argumenty z jeden a pouze jednu přetíženou skupinu.  
  
 V následujícím příkladu se pořídí z [aktivity přístupu k databázi](../../../docs/framework/windows-workflow-foundation/samples/database-access-activities.md) ukázku, existují dvě přetížení skupin: `ConnectionString` a `ConfigFileSectionName`. Pro tuto aktivitu platit, buď `ProviderName` a `ConnectionString` argumenty musí být vázán, nebo `ConfigName` argument, ale ne obojí.  
  
```  
Public class DbUpdate: AsyncCodeActivity  
{  
    [RequiredArgument]  
    [OverloadGroup("ConnectionString")]  
    [DefaultValue(null)]  
    public InArgument<string> ProviderName { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("ConnectionString")]  
    [DependsOn("ProviderName")]  
    [DefaultValue(null)]  
    public InArgument<string> ConnectionString { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("ConfigFileSectionName")]  
    [DefaultValue(null)]  
    public InArgument<string> ConfigName { get; set; }  
  
    [DefaultValue(null)]  
    public CommandType CommandType { get; set; }  
  
    [RequiredArgument]  
    public InArgument<string> Sql { get; set; }  
  
    [DependsOn("Sql")]  
    [DefaultValue(null)]  
    public IDictionary<string, Argument> Parameters { get; }  
  
    [DependsOn("Parameters")]  
    public OutArgument<int> AffectedRecords { get; set; }       
}  
```  
  
 Při definování přetížené skupiny:  
  
-   Přetížené skupiny nemůže být dílčí nebo ekvivalentní sadu jiného přetíženou skupinu.  
  
    > [!NOTE]
    >  Existuje jedna výjimka tohoto pravidla. Pokud přetížené skupiny jsou podmnožinou jiné skupiny přetížení a dílčí obsahuje argumenty, pouze pokud `RequiredArgument` je `false`, přetíženou skupinu je platný.  
  
-   Přetížené skupiny může dojít k překrytí, ale jedná se o chybu, pokud je určena průsečíkem skupiny obsahuje všechny požadované argumenty alespoň jednu z přetížených skupin. V předchozím příkladu `G2` a `G3` přetížení překrývajících se skupiny, ale protože je určena průsečíkem neobsahovala všechny argumenty jednoho nebo obou skupin toto byla platná.  
  
 Při vytváření vazby argumenty v přetížené skupiny:  
  
-   Přetížené skupiny se považuje za mez, zda mají všechny `RequiredArgument` argumenty ve skupině jsou vázána.  
  
-   Pokud má skupina nula `RequiredArgument` argumenty a aspoň jeden argument vázán, pak skupinu se považuje za s vazbou.  
  
-   Je chyba ověřování, pokud žádné přetížené skupiny jsou vázány, není-li jednu přetíženou skupinu nemá žádné `RequiredArgument` argumenty v ní.  
  
-   Jedná se o chybu mít více než jednu přetíženou skupinu vázán, který je, jsou vázána všechny požadované argumenty v jednu přetíženou skupinu a jsou svázaná některý argument v jiné skupině přetížení.
