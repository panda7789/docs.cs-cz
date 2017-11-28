---
title: "Vyžaduje argumenty a skupiny přetížení"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4ca3ed06-b9af-4b85-8b70-88c2186aefa3
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: fae9759faa6ae5e2fa65417c6ef5767330f6d9c6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="required-arguments-and-overload-groups"></a>Vyžaduje argumenty a skupiny přetížení
Aktivity lze nakonfigurovat tak, aby některé argumenty jsou povinné vázat pro aktivitu platná pro provedení. `RequiredArgument` Atribut slouží k označení, že některé argumenty u aktivit jsou povinné a `OverloadGroup` atribut slouží k seskupení kategorie povinnými argumenty. Pomocí atributy mohou aktivity tvůrci poskytnout jednoduché nebo komplexní aktivity ověření konfigurace.  
  
## <a name="using-required-arguments"></a>Pomocí povinnými argumenty  
 Použít `RequiredArgument` atribut v aktivitě, zda jsou požadované argumenty pomocí <xref:System.Activities.RequiredArgumentAttribute>. V tomto příkladu `Add` aktivity je definovaný, dvěma vyžaduje argumenty.  
  
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
  
 V jazyce XAML, povinnými argumenty jsou uvedeny i pomocí <xref:System.Activities.RequiredArgumentAttribute>. V tomto příkladu `Add` aktivity se definuje pomocí tří argumentů a používá <xref:System.Activities.Statements.Assign%601> aktivita k provedení operace přidání.  
  
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
  
 Pokud se používá aktivitu a není vázán buď povinnými argumenty se vrátí následující chybu ověřování.  
  
 **Nebyla zadána hodnota pro argument požadované aktivity 'Operand1'.**  
> [!NOTE]
>  [!INCLUDE[crabout](../../../includes/crabout-md.md)]informace o kontrole a zpracování chyb při ověřování a upozornění, v tématu [ověření aktivity vyvolání](../../../docs/framework/windows-workflow-foundation/invoking-activity-validation.md).  
  
## <a name="using-overload-groups"></a>Použití skupin přetížení  
 Přetížení skupiny zadejte metodu, která určuje, které kombinace argumenty jsou platné v aktivitě. Argumenty jsou seskupeny dohromady pomocí <xref:System.Activities.OverloadGroupAttribute>. Každou skupinu je zadaný název, který je zadán <xref:System.Activities.OverloadGroupAttribute>, aktivita je platná, pokud je vázána jen jednu sadu argumentů ve skupině přetížení. V následujícím příkladu převzaty z [OverloadGroups](../../../docs/framework/windows-workflow-foundation/samples/overloadgroups.md) ukázce `CreateLocation` třída definovaná.  
  
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
  
 Cílem této aktivity je zadejte umístění v USA. K tomuto účelu uživatele aktivity umístění můžete zadat pomocí jednoho ze tří skupin argumentů. Pokud chcete zadat platné kombinace argumenty, jsou definovány tři skupiny přetížení. `G1`obsahuje `Latitude` a `Longitude` argumenty. `G2`obsahuje `Street`, `City`, a `State`. `G3`obsahuje `Street` a `Zip`. `Name`je také požadovaný argument, ale není součástí skupiny přetížení. Pro tuto aktivitu platná `Name` by musel být vázána společně s všechny argumenty ze skupiny přetížení pouze jeden.  
  
 V následujícím příkladu převzaty z [databáze Access aktivity](../../../docs/framework/windows-workflow-foundation/samples/database-access-activities.md) ukázku, existují dvě přetížení skupin: `ConnectionString` a `ConfigFileSectionName`. Pro tuto aktivitu. Chcete-li být platný, buď `ProviderName` a `ConnectionString` argumenty musí být vázán, nebo `ConfigName` argument, ale ne obojí.  
  
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
  
 Při definování skupinu přetížení:  
  
-   Skupinu přetížení nemůže být podmnožinu nebo ekvivalentní sadu jiné skupiny pro přetížení.  
  
    > [!NOTE]
    >  Existuje jedna výjimka tohoto pravidla. Pokud skupinu přetížení je podmnožinou jiné přetížení skupiny a do něj podmnožinu obsahuje pouze argumenty kde `RequiredArgument` je `false`, pak přetížení skupina je neplatná.  
  
-   Přetížení skupiny může dojít k překrytí, ale jedná se o chybu, pokud průniku skupiny obsahuje všechny požadované argumenty jednoho nebo obou skupin přetížení. V předchozím příkladu `G2` a `G3` přetížení skupiny překryté, ale protože průnik neobsahoval všechny argumenty jednoho nebo obou skupin byla platná.  
  
 Při vytváření vazby argumenty ve skupině přetížení:  
  
-   Skupinu přetížení je považována za hranice, pokud všechny `RequiredArgument` argumenty ve skupině je vázána.  
  
-   Pokud skupina má nula `RequiredArgument` argumentů a alespoň jeden argument vázán, pak skupinu se považuje za hranice.  
  
-   Pokud žádné přetížení skupiny jsou svázané s Pokud jedna skupina přetížení neobsahuje žádné je chyba ověření `RequiredArgument` argumenty v ní.  
  
-   Jedná se o chybu do mají více než jednu skupinu přetížení vázán, který je, všechny požadované argumenty ve skupině jedním přetížením jsou svázané s a také vázán některý argument v jiné skupině přetížení.
