---
title: Aktivita propagace vlastnosti
ms.date: 03/30/2017
ms.assetid: 802196b7-1159-4c05-b41b-d3bfdfcc88d9
ms.openlocfilehash: 6e059a0d344e6c62833feaa890c459c141a49673
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2018
ms.locfileid: "43481134"
---
# <a name="property-promotion-activity"></a>Aktivita propagace vlastnosti
Tato ukázka poskytuje-ucelené řešení, která se integruje <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> funkci povýšení přímo do prostředí pro tvorbu pracovního postupu. Kolekce elementů konfigurace, aktivity pracovního postupu a pracovní postup rozšíření, která zjednodušuje použití funkce povýšení jsou k dispozici. Kromě toho vzorek obsahuje jednoduchý pracovní postup, který ukazuje, jak tuto kolekci použít.  
  
> [!NOTE]
>  Ukázky jsou k dispozici pouze pro vzdělávací účely. Nejsou určeny pro produkční prostředí a nebyly testovány v produkčním prostředí. Společnost Microsoft neposkytuje pro tyto ukázky technickou podporu.  
  
## <a name="prerequisites"></a>Požadavky  
  
-   Inicializovali <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> databáze  
  
-   [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]  
  
## <a name="sample-projects"></a>Ukázkové projekty  
  
-   **PropertyPromotionActivity** projekt obsahuje soubory vztahující se na podporu konkrétní konfigurační prvky, aktivity pracovního postupu a rozšíření pracovního postupu.  
  
-   **CounterServiceApplication** projekt obsahuje ukázkový pracovní postup, který používá **SqlWorkflowInstanceStorePromotion** projektu.  
  
-   Skript SQL (PropertyPromotionActivitySQLSample.sql), který musí být spuštěn proti <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> databáze.  
  
-   Soubor řešení, která propojuje dvě [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] projekty (`PropertyPromotionActivity.sln`)  
  
## <a name="to-set-up-and-run-the-sample"></a>K nastavení a spuštění ukázky  
  
1.  Inicializace databáze trvalosti pracovního postupu.  
  
    1.  Přejděte do adresáře vzorku (\WF\Basic\Persistence\PropertyPromotionActivity) a spusťte CreateInstanceStore.cmd.  
  
    2.  Pokud nejsou k dispozici oprávnění správce, vytvořte přihlášení systému SQL Server. V SQL Server Management Studio, přejděte na **zabezpečení**, **přihlášení**. Klikněte pravým tlačítkem na **přihlášení** a vytvořte nové přihlašovací údaje. Přidejte uživatele seznamu ACL k roli SQL tak, že otevřete **databází**, **třídy InstanceStore**, **zabezpečení**. Klikněte pravým tlačítkem na **uživatelé** a vyberte **nového uživatele**. Nastavte **přihlašovací jméno** uživateli vytvořené výše. Přidáte uživatele k členství role databáze System.Activities.DurableInstancing.InstanceStoreUsers (a ostatní). Všimněte si, že uživatel může existovat už (například objekt dbo uživatele).  
  
2.  Otevřete soubor řešení PropertyPromotionActivity.sln v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
3.  Pokud jste vytvořili v úložišti instancí v jiné databáze než místní instalace systému SQL Server Express, je nutné aktualizovat připojovací řetězec databáze. Příkaz ALTER souboru App.config v části **CounterServiceApplication** tak, že nastavíte hodnotu `connectionString` atribut na `sqlWorkflowInstanceStorePromotion` uzlu tak, aby odkazovala na databáze trvalosti, který byl inicializován v kroku 1.  
  
4.  Sestavte a spusťte řešení. Se spustit službu WF čítače a automaticky spustí instanci pracovního postupu.  
  
5.  Rychle vyberte všechny řádky v [dbo]. Zobrazení [counterService] databáze trvalosti (Toto zobrazení byl přidán spuštěním CreateInstanceStore.cmd v kroku 1). Zobrazí se výsledek podobný následujícímu nastavení:  
  
    |instanceId|CounterValue|CounterValueLastUpdated|  
    |----------------|------------------|-----------------------------|  
    |2FA2C302-929E-4C0D-8C25-768A3DA20CE5|12|2010-02-18 22:48:01.740|  
  
     Jak zachovat aktualizace zobrazení, můžete si všimnout, že CounterValue a CounterValueLastUpdated změnit každé dvě sekundy. Jedná se o interval, ve kterém se čítač aktualizuje sám. CounterValue a CounterValueLastUpdated představují propagované vlastnosti pro tento pracovní postup.  
  
## <a name="to-remove-the-sample"></a>Chcete-li odebrat vzorku  
  
-   Spusťte RemoveInstanceStore.cmd v adresáři ukázkové (\WF\Basic\Persistence\PropertyPromotionActivity).  
  
## <a name="understanding-this-sample"></a>Principy tuto ukázku  
 Ukázka obsahuje dva projekty a soubor SQL:  
  
-   **CounterServiceApplication** je konzolová aplikace, který je hostitelem služby jednoduchý čítač WF. Při přijetí jednosměrná zpráva prostřednictvím `Start` koncový bod, pracovní postup se počítá od 0 až 29 zvyšování hodnoty proměnné čítače každé dvě sekundy. Po každý přírůstek čítače pracovní postup se opakuje a propagované vlastnosti jsou aktualizovány v [dbo]. Zobrazení [counterService]. Při spuštění aplikace konzoly hostitelem služby pracovního postupu a odešle zprávu `Start` koncového bodu, vytváří instanci čítače WF.  
  
-   **PropertyPromotionActivity** je knihovny tříd, který obsahuje konfigurační prvky, aktivity pracovního postupu a pracovní postup rozšíření, která **CounterServiceApplication** používá.  
  
-   **PropertyPromotionActivitySQLSample.sql** vytvoří a přidá zobrazení [dbo]. [ CounterService] do databáze.  
  
### <a name="counterserviceapplication"></a>CounterServiceApplication  
  
#### <a name="using-the-sqlworkflowinstancestorepromotion-configuration-element"></a>Pomocí konfiguračního elementu SqlWorkflowInstanceStorePromotion  
 `SqlWorkflowInstanceStorePromotion` Element konfigurace dědí z `SqlWorkflowInstanceStore` prvek konfigurace, ale přidá další konfigurační prvek s názvem `promotionSets`. `promotionSets` Element umožňuje uživateli zadat propagované vlastnosti prostřednictvím konfigurace. Toto je konfigurační soubor, který se používá v rámci ukázky:  
  
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
  
 Zkontrolujte definici [dbo]. Zobrazení [counterService].  
  
```sql  
create view [dbo].[CounterService] as  
      select [InstanceId],  
 [Value1] as [CounterValue],  
 [Value2] as [CounterValueLastUpdated]  
      from [System.Activities.DurableInstancing].[InstancePromotedProperties]  
      where [PromotionName] = 'CounterService'  
go  
```  
  
 Pokud instance pracovního postupu budou dál problémy, vloží se řádek do `InstancePromotedProperties` zobrazení pro jednotlivé `PromotionSet` definované v konfiguraci. Tento řádek obsahuje všechny propagované vlastnosti `PromotionSet` (přesunuté jednu vlastnost pro každý sloupec). To `PromotionSet` označenými pomocí řazené kolekce členů: `InstanceId, PromotionName`. V tomto příkladu máme, jeden `PromotionSet` definované v konfiguraci, jehož název atributu je `CounterService`. Poznámka: Jak `PromotionName` hodnota sloupce je rovna hodnotě atribut name `PromotionSet` elementu.  
  
 Pořadí `promotedValue` prvky koreluje s umístění propagované vlastnosti `InstancePromotedProperties` zobrazení. `Count` je první `promotedValue` elementu. V důsledku toho je namapována na `Value1` sloupec `InstancePromotedProperties` zobrazení. `LastIncrementedAt` je druhý `promotedValue` elementu. V důsledku toho je namapována na `Value2` sloupec `InstancePromotedProperties` zobrazení.  
  
#### <a name="using-the-promotevalue-activity"></a>Použití aktivity PromoteValue  
 Zkontrolujte soubor CounterService.xamlx v Návrháři Windows Workflow Foundation. Všimněte si, že existují dva speciální aktivity v definici pracovního postupu: `PromoteValue<DateTime>` a `PromoteValue<Int32>`.  
  
 `PromoteValue<Int32>` Aktivita má jeho `Name` člena definovaného jako `Count`. Shoduje se s prvním `promotedValue` element v konfiguraci a má jeho `Value` definován jako `Counter` proměnné pracovního postupu. Když pracovní postup budou dál problémy, `Counter` proměnné pracovního postupu je trvalý jako propagovanou vlastnost do `Value1` sloupec `InstancePromotedProperties` zobrazení.  
  
 `PromoteValue<DateTime>` Aktivita má jeho `Name` člena definovaného jako `LastIncrementedAt`. Shoduje se s druhým `promotedValue` element v konfiguraci a má jeho `Value` definován jako `TimeLastIncremented` proměnné pracovního postupu. To znamená, že když pracovní postup budou dál problémy, hodnota `TimeLastIncremented` proměnné pracovního postupu se nastavit jako trvalý, jako propagovanou vlastnost do `Value2` sloupec `InstancePromotedProperties` zobrazení.  
  
 Všimněte si, že `PromotedValue` aktivity také obsahuje logický člena s názvem `ClearExistingPromotedData`. Pokud je tento člen nastaven na `true`, tato akce smaže všechny hodnoty propagované vlastnosti až k danému bodu v pracovním postupu. Například pokud sekvenční aktivity je definován jako následující:  
  
1.  PromoteValue {Name = "Count", hodnota = 3}  
  
2.  PromoteValue {Name = "LastIncrementedAt", hodnota = 1-1-2000}  
  
3.  Zachovat  
  
4.  PromoteValue {Name = "Count", hodnota = 4, ClearExistingPromotedData = true}  
  
5.  Zachovat  
  
 Na druhé trvalého přesunutá hodnota `Count` budou 4. Ale přesunutá hodnota `LastIncrementedAt` bude `NULL`. Pokud `ClearExistingPromotedData` nebyl nastaven na `true` kroku 4, pak po druhé trvalého přesunutá hodnotu Count by 4. V důsledku toho přesunutá hodnota `LastIncrementedAt` stále by šlo 1-1-2000.  
  
### <a name="propertypromotionactivity"></a>PropertyPromotionActivity  
 Tato knihovna tříd obsahuje následující veřejných tříd zjednodušení používání <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> funkci povýšení.  
  
#### <a name="promotevalue-class"></a>Třída PromoteValue  
 Tato třída podporuje jednu vlastnost. Název propagované vlastnosti by měl odpovídat názvu atributu `promotedValue` element v konfiguraci. Tato aktivita se dá použít v Návrháři pracovních postupů. Zobrazit CounterServiceApplication pro příklady použití.  
  
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
  
 ClearExistingPromotedData (Bool)  
 Vymaže všechny hodnoty, které byly přesunuty před této aktivity.  
  
 Název (řetězec)  
 Název, který představuje tuto vlastnost. Ten by měl odpovídat názvu atributu \<promotedValue > element v konfiguraci.  
  
 Hodnota (argument InArgument\<T >)  
 Proměnná / hodnota, které chcete uložit ve sloupci.  
  
#### <a name="promotevalues-class"></a>Třída PromoteValues  
 Podporuje více vlastností. Názvy propagované vlastnosti by měla odpovídat všechny atributy názvu v `promotedValue` prvky v konfiguraci. Využití je podobný `PromoteValue` aktivity, s výjimkou skutečnost, že ve stejnou dobu může být povýšen víc vlastností. Tuto aktivitu nelze použít v Návrháři pracovních postupů.  
  
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
 Je odvozen od `SqlWorkflowInstanceStoreBehavior`. Tato odvozená třída přidá vlastního účastníka trvalosti (také součástí této knihovny) jako rozšíření pracovního postupu. Implementace předchozích dvou aktivit pracovního postupu závisí na tomto vlastního účastníka trvalosti.  
  
```  
public class SqlWorkflowInstanceStorePromotionBehavior :  
             SqlWorkflowInstanceStoreBehavior, IServiceBehavior  
{  
        public void Promote(string name, IEnumerable<string> promoteAsSqlVariant,  
                            IEnumerable<string> promoteAsBinary)  
  
}  
```  
  
 Tato knihovna tříd obsahuje také `ConfigurationElement` implementace `SqlWorkflowInstanceStorePromotionElement` a vlastního účastníka trvalosti používají předchozí aktivity povýšení.  
  
### <a name="propertypromotionactivitysqlsample"></a>PropertyPromotionActivitySQLSample  
 Tento soubor SQL vytvoří `[dbo].[CounterService]` zobrazení kromě `[InstancePromotedProperties]` zobrazení pro dotazování na všechny instance, které mají sadu CounterService povýšení.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno ve vašem počítači. Před pokračováním zkontrolujte následující adresář (výchozí):  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři:  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Persistence\PropertyPromotionActivity`  
  
## <a name="see-also"></a>Viz také  
 [Hostování AppFabric a ukázky trvalosti](https://go.microsoft.com/fwlink/?LinkId=193961)
