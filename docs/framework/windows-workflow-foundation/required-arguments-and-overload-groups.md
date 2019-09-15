---
title: Povinné argumenty a skupiny přetížení
ms.date: 03/30/2017
ms.assetid: 4ca3ed06-b9af-4b85-8b70-88c2186aefa3
ms.openlocfilehash: 84384e90be0036036477d9b4249832f544e17d08
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989314"
---
# <a name="required-arguments-and-overload-groups"></a>Povinné argumenty a skupiny přetížení
Aktivity lze nakonfigurovat tak, aby byly určité argumenty vázány na to, aby byla aktivita platná pro provedení. Atribut slouží k označení, že jsou požadovány určité argumenty aktivity `OverloadGroup` , a atribut je použit k seskupení kategorií požadovaných argumentů společně. `RequiredArgument` Pomocí atributů můžou autoři aktivity poskytovat jednoduché nebo složité konfigurace ověřování aktivit.  
  
## <a name="using-required-arguments"></a>Použití požadovaných argumentů  
 Chcete-li `RequiredArgument` použít atribut v aktivitě, určete požadované argumenty pomocí <xref:System.Activities.RequiredArgumentAttribute>. V tomto příkladu `Add` je definována aktivita, která má dva povinné argumenty.  
  
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
  
 V jazyce XAML jsou povinné argumenty také označeny pomocí <xref:System.Activities.RequiredArgumentAttribute>. V tomto příkladu `Add` je aktivita definovaná pomocí tří argumentů a k provedení operace přidání <xref:System.Activities.Statements.Assign%601> používá aktivitu.  
  
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
  
 Pokud se aktivita používá a některý z požadovaných argumentů není vázaný na, vrátí se následující chyba ověřování.  
  
 **Nebyla zadána hodnota pro argument požadované aktivity ' Operand1 '.**  
> [!NOTE]
> Další informace o kontrole a zpracování chyb a upozornění ověřování najdete v tématu [vyvolání ověření aktivity](invoking-activity-validation.md).  
  
## <a name="using-overload-groups"></a>Použití skupin přetížení

Přetížené skupiny poskytují metodu pro indikaci, které kombinace argumentů jsou v aktivitě platné. Argumenty jsou seskupené dohromady pomocí <xref:System.Activities.OverloadGroupAttribute>. Každé skupině se předává název, který je určen v <xref:System.Activities.OverloadGroupAttribute>. Tato aktivita je platná, pokud je svázána pouze jedna sada argumentů v přetížené skupině. V následujícím příkladu `CreateLocation` je definována třída.  
  
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
  
 Cílem této aktivity je určit umístění v USA. Za tímto účelem může uživatel aktivity určit umístění pomocí jedné ze tří skupin argumentů. Chcete-li určit platnou kombinaci argumentů, jsou definovány tři přetížené skupiny. `G1`obsahuje argumenty `Longitude`a. `Latitude` `G2`obsahuje `Street`, `City`, a `State`. `G3`obsahuje `Street` a `Zip`. `Name`je také povinný argument, ale není součástí přetížené skupiny. Aby byla tato aktivita platná, `Name` musí být vázána společně se všemi argumenty z jedné a pouze jedné přetížené skupiny.  
  
 V následujícím příkladu pořízených z ukázky [aktivity přístupu k databázi](./samples/database-access-activities.md) existují dvě přetížené skupiny: `ConnectionString` a. `ConfigFileSectionName` Aby byla tato aktivita platná, musí `ProviderName` `ConfigName` být argumenty a `ConnectionString` buď vázané, nebo argument, ale ne obojí.  
  
```csharp  
public class DbUpdate: AsyncCodeActivity  
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
  
- Přetížená skupina nemůže být podmnožinou nebo ekvivalentní sadou jiné přetížené skupiny.  
  
    > [!NOTE]
    > Toto pravidlo obsahuje jednu výjimku. Pokud je přetížená skupina podmnožinou jiné přetížené skupiny a podmnožina obsahuje pouze argumenty `RequiredArgument` , `false`kde je, je přetížená skupina platná.  
  
- Přetížené skupiny se mohou překrývat, ale jedná se o chybu, pokud průnik skupin obsahuje všechny požadované argumenty jedné nebo obou skupin přetížení. V předchozím příkladu se `G2` překrývají skupiny a `G3` přetížení, ale vzhledem k tomu, že průnik neobsahoval všechny argumenty jedné nebo obou skupin, které byly platné.  
  
 Při vazbách argumentů v přetížené skupině:  
  
- Přetížená skupina se považuje za vázanou, `RequiredArgument` Pokud jsou všechny argumenty ve skupině svázané.  
  
- Pokud má skupina nulové `RequiredArgument` argumenty a alespoň jeden argument je vázaný, bude skupina považována za vázanou.  
  
- Jedná se o chybu ověřování, pokud nejsou svázány žádné přetížené skupiny, pokud v `RequiredArgument` ní nejsou žádné argumenty.  
  
- Je-li k dispozici více než jedna přetížená skupina, to znamená, že všechny požadované argumenty v jedné přetížené skupině jsou vázány a všechny argumenty v jiné přetížené skupině jsou také vázány.
