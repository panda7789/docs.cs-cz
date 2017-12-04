---
title: "Vlastnost povýšení aktivity"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 802196b7-1159-4c05-b41b-d3bfdfcc88d9
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3e1237c0732b5422034db7c83c665c57c48486d7
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="property-promotion-activity"></a>Vlastnost povýšení aktivity
Tato ukázka poskytuje-komplexní řešení, která integruje <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> funkci povýšení přímo do pracovního postupu pro tvorbu prostředí. Soubor konfigurace – elementy, aktivity pracovního postupu a pracovní postup rozšíření, které usnadňují používání funkce povýšení jsou k dispozici. Kromě toho vzorek obsahuje jednoduché pracovní postup, který ukazuje, jak lze pomocí této kolekce.  
  
> [!NOTE]
>  Ukázky jsou uvedeny pouze pro vzdělávací účely. Nejsou určeny pro produkční prostředí a nebyly testovány v produkčním prostředí. Společnost Microsoft neposkytuje pro tyto ukázky technickou podporu.  
  
## <a name="prerequisites"></a>Požadavky  
  
-   Inicializovali <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> databáze  
  
-   [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]  
  
## <a name="sample-projects"></a>Ukázkové projekty  
  
-   **PropertyPromotionActivity** projekt obsahuje soubory vztahující se k povýšení konkrétní konfigurační prvky, aktivity pracovního postupu a pracovní postup rozšíření.  
  
-   **CounterServiceApplication** projekt obsahuje ukázkový pracovní postup, který používá **SqlWorkflowInstanceStorePromotion** projektu.  
  
-   Skript SQL (PropertyPromotionActivitySQLSample.sql), který musí být spuštěn proti <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> databáze.  
  
-   Soubor řešení, který odkazuje dva [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] projekty (`PropertyPromotionActivity.sln`)  
  
## <a name="to-set-up-and-run-the-sample"></a>Jak nastavit a spustit ukázku  
  
1.  Inicializuje databázi trvalost pracovního postupu.  
  
    1.  Přejděte do adresáře ukázkové (\WF\Basic\Persistence\PropertyPromotionActivity) a spusťte CreateInstanceStore.cmd.  
  
    2.  Pokud nejsou k dispozici oprávnění správce, vytvořte přihlášení systému SQL Server. V systému SQL Server Management Studio přejděte do **zabezpečení**, **přihlášení**. Klikněte pravým tlačítkem na **přihlášení** a vytvořte nové přihlašovací údaje. Přidat seznamu ACL uživatele k roli SQL otevřením **databáze**, **InstanceStore**, **zabezpečení**. Klikněte pravým tlačítkem na **uživatelé** a vyberte **nového uživatele**. Nastavte **přihlašovací jméno** uživateli vytvořili výše. Přidejte uživatele k členství role databáze System.Activities.DurableInstancing.InstanceStoreUsers (a dalších). Všimněte si, že tento uživatel může existovat již (například dbo uživatele).  
  
2.  Otevřete soubor řešení PropertyPromotionActivity.sln v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
3.  Pokud jste vytvořili instanci úložiště do jiné databáze než místní instalace systému SQL Server Express, je nutné aktualizovat připojovací řetězec databáze. Příkaz ALTER souboru App.config v části **CounterServiceApplication** nastavením hodnotu `connectionString` atributu u `sqlWorkflowInstanceStorePromotion` uzlu tak, aby odkazoval na databázi trvalost, který byl inicializován v kroku 1.  
  
4.  Sestavení a spuštění řešení. To se spustit službu čítač WF a automaticky spustí instanci pracovního postupu.  
  
5.  Rychle vyberte všechny řádky v [dbo]. Zobrazení [counterService] v databázi trvalost (v tomto zobrazení byl přidán spuštěním CreateInstanceStore.cmd v kroku 1). Zobrazí se podobné následujícímu sadě výsledků dotazu:  
  
    |identifikátor instanceId|Přepočtené|CounterValueLastUpdated|  
    |----------------|------------------|-----------------------------|  
    |2FA2C302-929E-4C0D-8C25-768A3DA20CE5|12|2010-02-18 22:48:01.740|  
  
     Jak můžete pokračovat v obnovování zobrazení, si všimnete, že přepočtené a CounterValueLastUpdated změnit každé dvě sekundy. Toto je interval, ve kterém čítač se aktualizuje sám. Přepočtené a CounterValueLastUpdated představují propagovaných vlastnosti pro tento pracovní postup.  
  
## <a name="to-remove-the-sample"></a>Chcete-li odebrat vzorku  
  
-   Spusťte RemoveInstanceStore.cmd v adresáři ukázkové (\WF\Basic\Persistence\PropertyPromotionActivity).  
  
## <a name="understanding-this-sample"></a>Vysvětlení této ukázky  
 Ukázka obsahuje dva projekty a soubor SQL:  
  
-   **CounterServiceApplication** je konzolová aplikace, který je hostitelem služby jednoduchý čítač WF. Po přijetí jednosměrný zprávy prostřednictvím `Start` koncový bod, pracovní postup počty od 0 do 29, zvyšování proměnnou čítač každé dvě sekundy. Po každé přírůstek čítač potrvají pracovního postupu a propagovaných vlastnosti jsou aktualizovány v [dbo]. [CounterService] zobrazení. Při spuštění konzolové aplikace hostuje službu WF a odešle zprávu, která `Start` koncový bod, vytvoření instance čítače WF.  
  
-   **PropertyPromotionActivity** je knihovna tříd, který obsahuje konfigurační prvky, aktivity pracovního postupu a pracovní postup rozšíření, **CounterServiceApplication** používá.  
  
-   **PropertyPromotionActivitySQLSample.sql** vytvoří a přidá zobrazení [dbo]. [ CounterService] do databáze.  
  
### <a name="counterserviceapplication"></a>CounterServiceApplication  
  
#### <a name="using-the-sqlworkflowinstancestorepromotion-configuration-element"></a>Pomocí elementu SqlWorkflowInstanceStorePromotion konfigurace  
 `SqlWorkflowInstanceStorePromotion` Konfigurace element dědí z `SqlWorkflowInstanceStore` konfigurace elementu, ale přidá další konfiguraci prvek s názvem `promotionSets`. `promotionSets` Prvek umožní uživateli zadat propagovaných vlastnosti prostřednictvím konfigurace. Toto je konfigurační soubor, který je používán v ukázkovém:  
  
```xml  
<sqlWorkflowInstanceStorePromotion connectionString ="Data Source=.;Initial Catalog=SqlWorkflowInstanceStoreTest;Integrated Security=True;">  
  <promotionSets>  
    <promotionSet name="CounterService">  
      <promotedValue propertyName="Count"/>  
      <promotedValue propertyName="LastIncrementedAt"/>  
    </promotionSet>  
  </promotionSets>  
</sqlWorkflowInstanceStorePromotion>  
```  
  
 Zkontrolujte definici [dbo]. [CounterService] zobrazení.  
  
```sql  
create view [dbo].[CounterService] as  
      select [InstanceId],  
 [Value1] as [CounterValue],  
 [Value2] as [CounterValueLastUpdated]  
      from [System.Activities.DurableInstancing].[InstancePromotedProperties]  
      where [PromotionName] = 'CounterService'  
go  
```  
  
 Když instanci pracovního postupu přetrvává, vloží se řádek do `InstancePromotedProperties` zobrazení pro každý `PromotionSet` definované v konfiguraci. Tento řádek obsahuje všechny propagovaných vlastnosti `PromotionSet` (povýší jednu vlastnost pro každý sloupec). To `PromotionSet` je s klíči řazenou kolekci členů: `InstanceId, PromotionName`. V této ukázce jsme mít jeden `PromotionSet` definované v konfiguraci, jehož název atributu je `CounterService`. Poznámka: Jak `PromotionName` hodnota sloupce je rovna atribut názvu `PromotionSet` elementu.  
  
 Pořadí `promotedValue` elementy koreluje s propagovaných vlastností v umístění `InstancePromotedProperties` zobrazení. `Count`je první `promotedValue` elementu. V důsledku toho je namapovaný na `Value1` sloupec v `InstancePromotedProperties` zobrazení. `LastIncrementedAt`je druhá `promotedValue` elementu. V důsledku toho je namapovaný na `Value2` sloupec v `InstancePromotedProperties` zobrazení.  
  
#### <a name="using-the-promotevalue-activity"></a>Pomocí aktivity PromoteValue  
 Zkontrolujte v souboru CounterService.xamlx ve [!INCLUDE[wf2](../../../../includes/wf2-md.md)] Designer. Definice pracovního postupu jsou speciální dvě aktivity: `PromoteValue<DateTime>` a `PromoteValue<Int32>`.  
  
 `PromoteValue<Int32>` Aktivita má jeho `Name` člen definován jako `Count`. To odpovídá s prvním `promotedValue` element v konfiguraci a má jeho `Value` definován jako `Counter` proměnné pracovního postupu. Když pracovní postup potrvají, `Counter` proměnné pracovního postupu je uchován jako propagovaných vlastnost do `Value1` sloupec `InstancePromotedProperties` zobrazení.  
  
 `PromoteValue<DateTime>` Aktivita má jeho `Name` člen definován jako `LastIncrementedAt`. To odpovídá s druhou `promotedValue` element v konfiguraci a má jeho `Value` definován jako `TimeLastIncremented` proměnné pracovního postupu. To znamená, že když pracovní postup přetrvává, hodnota `TimeLastIncremented` proměnné pracovního postupu bude natrvalo jako propagovaných vlastnost do `Value2` sloupec `InstancePromotedProperties` zobrazení.  
  
 Všimněte si, že `PromotedValue` aktivita má také Boolean člena s názvem `ClearExistingPromotedData`. Když je tento člen nastavená na `true`, zruší všechny hodnoty vlastností propagovaných až tento bod v pracovním postupu. Například pokud aktivitu pořadí je definován jako takto:  
  
1.  PromoteValue {Name = "Count", hodnota = 3}  
  
2.  PromoteValue {Name = "LastIncrementedAt", hodnota = 1-1-2000}  
  
3.  Zachovat  
  
4.  PromoteValue {Name = "Count", hodnota = 4, ClearExistingPromotedData = true}  
  
5.  Zachovat  
  
 Na druhé zachovat povýšeného hodnota `Count` 4. Ale propagovaných hodnota `LastIncrementedAt` bude `NULL`. Pokud `ClearExistingPromotedData` nebyl nastaven na `true` kroku 4, pak po druhé zachovat povýšeného hodnotu pro počet by bylo 4. V důsledku toho propagovaných hodnota `LastIncrementedAt` by však bylo 1-1-2000.  
  
### <a name="propertypromotionactivity"></a>PropertyPromotionActivity  
 Tato knihovna tříd obsahuje následující veřejné třídy ke zjednodušení použití <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> funkci povýšení.  
  
#### <a name="promotevalue-class"></a>PromoteValue – třída  
 Tato třída podporuje jednu vlastnost. Název propagovaných vlastnosti by měl odpovídat názvu atributu `promotedValue` element v konfiguraci. Tato aktivita lze použít v Návrháři pracovních postupů. V tématu CounterServiceApplication pro příklad použití.  
  
```csharp  
public class PromoteValue<T> : CodeActivity  
{  
    public PromoteValue()  
    {  
    }  
  
    public bool ClearExistingPromotedData { get; set; }  
    public string Name { get; set; }  
    public InArgument<T> Value { get; set; }  
}  
```  
  
 ClearExistingPromotedData (logická hodnota)  
 Vymaže všechny hodnoty, které byly povýší před této aktivity.  
  
 název (string)  
 Název, který představuje tuto vlastnost. Mělo by to odpovídat atribut názvu \<promotedValue > element v konfiguraci.  
  
 Hodnota (InArgument\<T >)  
 Proměnná / hodnota, které chcete uložit ve sloupci.  
  
#### <a name="promotevalues-class"></a>PromoteValues – třída  
 Zvýší úroveň více vlastností. Názvy vlastností propagovaných musí odpovídat všechny atributy názvu v `promotedValue` elementy v konfiguraci. Využití je podobná `PromoteValue` aktivity, s výjimkou fakt, že můžete zvýšit úroveň více vlastností ve stejnou dobu. Tuto aktivitu nelze použít v Návrháři pracovních postupů.  
  
```  
public class PromoteValues : CodeActivity  
{  
    public PromoteValues()  
    {  
        this.ValuesToPromote = new Dictionary<string, InArgument>();  
    }  
  
    public bool ClearExistingPromotedData { get; set; }  
    public IDictionary<string, InArgument> ValuesToPromote { get; set; }  
}  
```  
  
#### <a name="sqlworkflowinstancestorepromotionbehavior"></a>SqlWorkflowInstanceStorePromotionBehavior  
 Odvozená z `SqlWorkflowInstanceStoreBehavior`. Tato odvozená třída přidá vlastní trvalost účastník (také součástí této knihovny) jako rozšíření pracovního postupu. Implementace předchozích dvou aktivit pracovního postupu spoléhá na tento účastník vlastní trvalost.  
  
```  
public class SqlWorkflowInstanceStorePromotionBehavior :  
             SqlWorkflowInstanceStoreBehavior, IServiceBehavior  
{  
        public void Promote(string name, IEnumerable<string> promoteAsSqlVariant,  
                            IEnumerable<string> promoteAsBinary)  
  
}  
```  
  
 Tato knihovna třída také obsahuje `ConfigurationElement` implementace `SqlWorkflowInstanceStorePromotionElement` , která vlastní trvalost používá předchozí aktivity povýšení.  
  
### <a name="propertypromotionactivitysqlsample"></a>PropertyPromotionActivitySQLSample  
 Vytvoří tento soubor SQL `[dbo].[CounterService]` zobrazení kromě `[InstancePromotedProperties]` zobrazení pro dotaz na všechny instance, které mají sadu CounterService povýšení.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalován ve vašem počítači. Před pokračováním zkontrolovat na následující adresář (výchozí):  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři:  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Persistence\PropertyPromotionActivity`  
  
## <a name="see-also"></a>Viz také  
 [Ukázky trvalosti a hostování AppFabric](http://go.microsoft.com/fwlink/?LinkId=193961)
