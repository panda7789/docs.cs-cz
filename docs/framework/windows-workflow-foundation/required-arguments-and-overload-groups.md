---
title: Povinné argumenty a skupiny přetížení
ms.date: 03/30/2017
ms.assetid: 4ca3ed06-b9af-4b85-8b70-88c2186aefa3
ms.openlocfilehash: 4eb62306f52b8ff890d5a5333c3789bd84ad7f60
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142937"
---
# <a name="required-arguments-and-overload-groups"></a>Povinné argumenty a skupiny přetížení
Aktivity lze nakonfigurovat tak, aby určité argumenty musí být vázány na aktivitu, která má být platná pro spuštění. Atribut `RequiredArgument` se používá k označení, že některé argumenty `OverloadGroup` na aktivitu jsou požadovány a atribut se používá k seskupení kategorií požadovaných argumentů dohromady. Pomocí atributů mohou autoři aktivity poskytovat jednoduché nebo složité konfigurace ověření aktivity.  
  
## <a name="using-required-arguments"></a>Použití požadovaných argumentů  
 Chcete-li `RequiredArgument` použít atribut v aktivitě, <xref:System.Activities.RequiredArgumentAttribute>označte požadované argumenty pomocí . V tomto příkladu je definována aktivita, `Add` která má dva požadované argumenty.  
  
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
  
 V XAML jsou požadované argumenty také <xref:System.Activities.RequiredArgumentAttribute>indikovány pomocí . V tomto `Add` příkladu je aktivita definována <xref:System.Activities.Statements.Assign%601> pomocí tří argumentů a používá aktivitu k provedení operace přidání.  
  
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
  
 Pokud je aktivita použita a některý z požadovaných argumentů není vázán, je vrácena následující chyba ověření.  
  
 **Hodnota pro argument požadované aktivity Operand1 nebyla zadána.**  
> [!NOTE]
> Další informace o kontrole a zpracování chyb a upozornění ověření ověření naleznete [v tématu Vyvolání ověření aktivity](invoking-activity-validation.md).  
  
## <a name="using-overload-groups"></a>Použití skupin přetížení

Skupiny přetížení poskytují metodu pro označení, které kombinace argumentů jsou platné v aktivitě. Argumenty jsou seskupeny <xref:System.Activities.OverloadGroupAttribute>pomocí . Každá skupina má název, který <xref:System.Activities.OverloadGroupAttribute>je určen . Aktivita je platná, pokud jsou vázány pouze jedna sada argumentů ve skupině přetížení. V následujícím příkladu `CreateLocation` je definována třída.  
  
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
  
 Cílem této činnosti je určit umístění v USA. Chcete-li to provést, uživatel aktivity můžete zadat umístění pomocí jedné ze tří skupin argumentů. Chcete-li zadat platné kombinace argumentů, jsou definovány tři skupiny přetížení. `G1`obsahuje `Latitude` argumenty a. `Longitude` `G2`obsahuje `Street` `City`, `State`a . `G3`obsahuje `Street` `Zip`a . `Name`je také povinný argument, ale není součástí skupiny přetížení. Aby byla tato aktivita platná, `Name` musela by být spojena se všemi argumenty z jedné a pouze jedné skupiny přetížení.  
  
 V následujícím příkladu převzaty z access [aktivity databáze](./samples/database-access-activities.md) `ConnectionString` ukázky existují dvě skupiny přetížení: a `ConfigFileSectionName`. Aby byla tato aktivita `ProviderName` platná, musí být argumenty a `ConnectionString` vázány nebo `ConfigName` argument, nikoli však oba.  
  
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
  
 Při definování skupiny přetížení:  
  
- Skupina přetížení nemůže být podmnožinou nebo ekvivalentní sadou jiné skupiny přetížení.  
  
    > [!NOTE]
    > Existuje jedna výjimka z tohoto pravidla. Pokud skupina přetížení je podmnožinou jiné skupiny přetížení a `RequiredArgument` podmnožina obsahuje pouze argumenty, kde je `false`, pak skupina přetížení je platný.  
  
- Přetížení skupiny mohou překrývat, ale je chyba, pokud průsečík skupin obsahuje všechny požadované argumenty jedné nebo obou skupin přetížení. V předchozím `G2` příkladu `G3` se překrývaly skupiny přetížení a skupiny přetížení, ale protože průsečík neobsahoval všechny argumenty jedné nebo obou skupin, byl tento počet platný.  
  
 Při vazby argumenty ve skupině přetížení:  
  
- Skupina přetížení je považována za `RequiredArgument` vázanou, pokud jsou všechny argumenty ve skupině vázány.  
  
- Pokud skupina má `RequiredArgument` nulové argumenty a alespoň jeden argument vázán, pak je skupina považována za vázanou.  
  
- Je chyba ověření, pokud jsou vázány žádné skupiny přetížení, pokud jedna skupina přetížení nemá žádné `RequiredArgument` argumenty v něm.  
  
- Je chyba mít více než jednu skupinu přetížení vázána, to znamená, že všechny požadované argumenty v jedné skupině přetížení jsou vázány a jakýkoli argument v jiné skupině přetížení je také vázán.
