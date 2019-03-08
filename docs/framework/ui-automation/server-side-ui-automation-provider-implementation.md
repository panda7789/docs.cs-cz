---
title: Implementace zprostředkovatele automatizace uživatelského rozhraní na straně serveru
ms.date: 03/30/2017
helpviewer_keywords:
- server-side UI Automation provider implementation
- UI Automation, server-side provider implementation
- provider implementation, UI Automation
ms.assetid: 6acc6d08-bd67-4e2e-915c-9c1d34eb86fe
ms.openlocfilehash: df2c1fcd6c84b7670c53a8f06f97c2ea46b8b33d
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/08/2019
ms.locfileid: "57679408"
---
# <a name="server-side-ui-automation-provider-implementation"></a>Implementace zprostředkovatele automatizace uživatelského rozhraní na straně serveru
> [!NOTE]
>  Tato dokumentace je určená pro vývojáře rozhraní .NET Framework, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tříd definovaných v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], naleznete v tématu [Windows Automation API: Automatizace uživatelského rozhraní](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Tato část popisuje, jak pro implementaci zprostředkovatele automatizace uživatelského rozhraní na straně serveru pro vlastní ovládací prvek.  
  
 Implementace pro elementy Windows Presentation Foundation (WPF) a jiné-[!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] prvky (například určená pro [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)]) je fundamentálně odlišný způsob. [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] prvky poskytují podporu pro [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] prostřednictvím třídy odvozené od <xref:System.Windows.Automation.Peers.AutomationPeer>. Jinou hodnotu než[!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] prvky poskytují podporu prostřednictvím implementace rozhraní poskytovatele.  
  
<a name="Security_Considerations"></a>   
## <a name="security-considerations"></a>Důležité informace o zabezpečení  
 Poskytovatelé by měly být napsány tak, aby mohou pracovat v prostředí s částečným vztahem důvěryhodnosti. Protože UIAutomationClient.dll není nakonfigurované na spouštění v částečném vztahu důvěryhodnosti, zprostředkovatele kódu nesmí odkazovat na toto sestavení. Pokud už existoval, takže kód může spustit v prostředí úplného vztahu důvěryhodnosti, ale dojde k selhání v prostředí s částečným vztahem důvěryhodnosti.  
  
 Zejména, nepoužívejte pole z třídy v UIAutomationClient.dll jako například sítě na <xref:System.Windows.Automation.AutomationElement>. Místo toho použijte odpovídající pole z tříd v UIAutomationTypes.dll, jako například <xref:System.Windows.Automation.AutomationElementIdentifiers>.  
  
<a name="Provider_Implementation_by_WPF_Elements"></a>   
## <a name="provider-implementation-by-windows-presentation-foundation-elements"></a>Používaná implementace poskytovatele elementy Windows Presentation Foundation  
 Další informace o tomto tématu najdete v tématu [automatizace uživatelského rozhraní vlastního ovládacího prvku WPF](../../../docs/framework/wpf/controls/ui-automation-of-a-wpf-custom-control.md).  
  
<a name="Provider_Implementation_by_non_WPF_Elements"></a>   
## <a name="provider-implementation-by-non-wpf-elements"></a>Používaná implementace poskytovatele ve WPF elementy  
 Vlastní ovládací prvky, které nejsou součástí [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] rozhraní framework, ale které jsou zapsané ve spravovaném kódu (většinou jsou [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] ovládací prvky), poskytují podporu pro [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] prostřednictvím implementace rozhraní. Každý prvek musí implementovat alespoň jedno z rozhraní uvedená v první tabulce v další části. Kromě toho pokud element podporuje jeden nebo více vzorů ovládacích prvků, musí implementovat rozhraní vhodná pro každý – vzor ovládacích prvků.  
  
 Vaše [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] projektu zprostředkovatele musí odkazovat na následující sestavení:  
  
-   UIAutomationProviders.dll  
  
-   UIAutomationTypes.dll  
  
-   WindowsBase.dll  
  
  
<a name="Provider_Interfaces"></a>   
### <a name="provider-interfaces"></a>Rozhraní poskytovatele  
 Každý [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] poskytovatel musí implementovat jedno z následujících rozhraní.  
  
|Rozhraní|Popis|  
|---------------|-----------------|  
|<xref:System.Windows.Automation.Provider.IRawElementProviderSimple>|Poskytuje funkce pro ovládací prvek jednoduché hostované v okně, včetně podpory pro vzorů ovládacích prvků a vlastností.|  
|<xref:System.Windows.Automation.Provider.IRawElementProviderFragment>|Dědí z <xref:System.Windows.Automation.Provider.IRawElementProviderSimple>. Přidá funkce pro element v komplexní ovládací prvek, jako je navigace v rámci fragment, nastavení fokusu a vrací ohraničující obdélník elementu.|  
|<xref:System.Windows.Automation.Provider.IRawElementProviderFragmentRoot>|Dědí z <xref:System.Windows.Automation.Provider.IRawElementProviderFragment>. Přidá funkce pro kořenový element v komplexní ovládací prvek, včetně lokalizuje podřízený element na zadaných souřadnicích a nastavení stavu fokus pro celý ovládací prvek.|  
  
 Následující rozhraní poskytují další funkce, ale nejsou vyžadovány k implementaci.  
  
|Rozhraní|Popis|  
|---------------|-----------------|  
|<xref:System.Windows.Automation.Provider.IRawElementProviderAdviseEvents>|Umožňuje poskytovateli ke sledování požadavků pro události.|  
|<xref:System.Windows.Automation.Provider.IRawElementProviderHwndOverride>|Umožňuje založené na oknech elementů v rámci přemístění [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu fragmentu.|  
  
 Všechna rozhraní v <xref:System.Windows.Automation.Provider> obor názvů jsou určené pro podporu řízení vzor.  
  
<a name="Requirements_for_Non_WPF_Providers"></a>   
### <a name="requirements-for-non-wpf-providers"></a>Požadavky pro poskytovatele bez WPF  
 Chcete-li komunikovat s [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], ovládací prvek musí implementovat následující hlavní oblasti funkce:  
  
|Funkce|Implementace|  
|-------------------|--------------------|  
|Vystavení zprostředkovatele pro [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|V reakci na WM_GETOBJECT zpráva odeslaná do okna ovládacího prvku, vrátí objekt, který implementuje <xref:System.Windows.Automation.Provider.IRawElementProviderSimple> (nebo odvozené rozhraní). Pro fragmenty musí se jednat zprostředkovatele pro kořenovou fragment.|  
|Zadejte hodnoty vlastností|Implementace <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPropertyValue%2A> rozšířit nebo přepsat hodnoty.|  
|Umožnění spolupráce klienta služby pro interakci s ovládacím prvkem|Implementovat rozhraní, které podporují vzorů ovládacích prvků, jako je například <xref:System.Windows.Automation.Provider.IInvokeProvider>. Vrátí tito poskytovatelé vzor ve vaší implementaci <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A>.|  
|Vyvolávání událostí|Voláním statické metody <xref:System.Windows.Automation.Provider.AutomationInteropProvider> k vyvolání události, který může naslouchat klienta.|  
|Povolit navigaci a zaměřuje se v rámci fragment|Implementace <xref:System.Windows.Automation.Provider.IRawElementProviderFragment> pro každý prvek v rámci fragment. (Není potřeba pro prvky, které nejsou součástí fragment.)|  
|Povolit zaměření a umístění podřízený element v fragment|Implementace <xref:System.Windows.Automation.Provider.IRawElementProviderFragmentRoot>. (Není potřeba pro prvky, které není fragment kořeny.)|  
  
<a name="Property_Values_in_Non_WPF_Providers"></a>   
### <a name="property-values-in-non-wpf-providers"></a>Hodnoty vlastností ve zprostředkovatelích bez WPF  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zprostředkovatelé pro vlastní ovládací prvky, musí podporovat některé vlastnosti, které lze použít systém automatizace, stejně jako u klientských aplikací. Pro prvky, které jsou hostované v systému windows (HWND) [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] můžete načíst některé vlastnosti z okna výchozího zprostředkovatele, ale ostatní musí získat od vlastního zprostředkovatele.  
  
 Zprostředkovatelé pro ovládací prvky na základě HWND nemusíte obvykle poskytují následující vlastnosti (identifikovaných podle hodnoty polí):  
  
-   <xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>  
  
-   <xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>  
  
-   <xref:System.Windows.Automation.AutomationElementIdentifiers.ProcessIdProperty>  
  
-   <xref:System.Windows.Automation.AutomationElementIdentifiers.ClassNameProperty>  
  
-   <xref:System.Windows.Automation.AutomationElementIdentifiers.HasKeyboardFocusProperty>  
  
-   <xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>  
  
-   <xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>  
  
-   <xref:System.Windows.Automation.AutomationElementIdentifiers.IsPasswordProperty>  
  
-   <xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>  
  
-   <xref:System.Windows.Automation.AutomationElementIdentifiers.RuntimeIdProperty>  
  
> [!NOTE]
>  <xref:System.Windows.Automation.AutomationElementIdentifiers.RuntimeIdProperty> Jednoduchý prvek nebo fragment kořenové hostované v okně se získávají z okna; však fragment prvky pod kořenovým adresářem (jako je například seznam položek v seznamu), musíte zadat své vlastní identifikátory. Další informace naleznete v tématu <xref:System.Windows.Automation.Provider.IRawElementProviderFragment.GetRuntimeId%2A>.  
>   
>  <xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty> Má být vrácen pro poskytovatele hostované v [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] ovládacího prvku. V takovém případě může být okno výchozího zprostředkovatele nelze načíst správnou hodnotu.  
>   
>  <xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty> Obvykle získáte ho od poskytovatele hostitele. Například pokud vlastního ovládacího prvku je odvozena z <xref:System.Windows.Forms.Control>, název je odvozen z `Text` vlastnost ovládacího prvku.  
  
 Příklad kódu naleznete v tématu [vrácení vlastností ze zprostředkovatele automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/return-properties-from-a-ui-automation-provider.md).  
  
<a name="Events_in_Non_WPF_Providers"></a>   
### <a name="events-in-non-wpf-providers"></a>Události ve zprostředkovatelích bez WPF  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] poskytovatelé by měl vyvolat události upozornění na změny ve stavu uživatelského rozhraní klientské aplikace. Následující metody se používají pro vyvolání události.  
  
|Metoda|Popis|  
|------------|-----------------|  
|<xref:System.Windows.Automation.Provider.AutomationInteropProvider.RaiseAutomationEvent%2A>|Vyvolá různé události, včetně událostí aktivovaných změnou vzorů ovládacích prvků.|  
|<xref:System.Windows.Automation.Provider.AutomationInteropProvider.RaiseAutomationPropertyChangedEvent%2A>|Vyvolá událost, když [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] je změněna vlastnost.|  
|<xref:System.Windows.Automation.Provider.AutomationInteropProvider.RaiseStructureChangedEvent%2A>|Vyvolá událost při struktury [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] strom změnil; například tím, že odstranění nebo přidání elementu.|  
  
 Účelem události je informovat klienta o něco probíhat [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)]to, jestli se aktivuje aktivitu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] samotný systém. Například událost identifikovaný <xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent> by měla být zvýšena pokaždé, když se ovládací prvek je vyvolána, buď prostřednictvím přímé uživatelský vstup nebo volající aplikace klienta <xref:System.Windows.Automation.InvokePattern.Invoke%2A>.  
  
 Za účelem optimalizace výkonu můžete zprostředkovatele selektivně vyvolat události, nebo vůbec vyvolat žádné události. Pokud žádné klientská aplikace je zaregistrovaná a může přijímat. Následující metody se používají pro optimalizaci.  
  
|Metoda|Popis|  
|------------|-----------------|  
|<xref:System.Windows.Automation.Provider.AutomationInteropProvider.ClientsAreListening%2A>|Tato statická vlastnost určuje, zda všechny klientské aplikace předplacenou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] události.|  
|<xref:System.Windows.Automation.Provider.IRawElementProviderAdviseEvents>|Poskytovatele implementace tohoto rozhraní v kořenovém adresáři fragment umožňuje doporučuje, když klienti vytvářet a rušit registraci obslužné rutiny událostí pro události na fragment.|  
  
<a name="Non_WPF_Provider_Navigation"></a>   
### <a name="non-wpf-provider-navigation"></a>Navigace bez WPF poskytovatele  
 Zprostředkovatelé pro jednoduché ovládací prvky jako tlačítka s vlastní hostované v okně (HWND) není nutné k podpoře navigace v rámci [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu. Navigace do a z elementu zařizuje služba výchozího zprostředkovatele pro okno hostitele, které je zadáno v provádění <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.HostRawElementProvider%2A>. Při implementaci zprostředkovatele pro komplexní vlastního ovládacího prvku, ale musí podporovat navigace mezi kořenový uzel ve fragmentu a jejích potomků a mezi uzly na stejné úrovni.  
  
> [!NOTE]
>  Prvky fragmentu než kořenový musí vrátit `null` odkazovat z <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.HostRawElementProvider%2A>, protože nejsou přímo hostovány v okně a žádná výchozí zprostředkovatel může nepodporují navigaci pomocí do a z nich.  
  
 Struktura fragment je určeno v implementaci <xref:System.Windows.Automation.Provider.IRawElementProviderFragment.Navigate%2A>. Pro všechny možné směry z každé fragment tato metoda vrací objekt zprostředkovatele pro element v tomto směru. Pokud neexistuje žádný element v tomto směru, metoda vrátí `null` odkaz.  
  
 Fragment kořenové podporuje navigaci pouze na podřízené prvky. Například vrátí pole se seznamem první položku v seznamu Pokud je směr <xref:System.Windows.Automation.Provider.NavigateDirection.FirstChild>a poslední položky, pokud je směr <xref:System.Windows.Automation.Provider.NavigateDirection.LastChild>. Fragment kořenové nepodporuje přechod na nadřazenou položku nebo na stejné úrovni; To je zpracována zprostředkovatelem oken hostitele.  
  
 Prvky fragment, které nejsou kořen musí podporovat navigace pro nadřazenou a na všechny na stejné úrovni a podřízené položky, které mají.  
  
<a name="Non_WPF_Provider_Reparenting"></a>   
### <a name="non-wpf-provider-reparenting"></a>Změna nadřazení poskytovatele bez WPF  
 Automaticky otevíraná okna jsou ve skutečnosti nejvyšší úrovně systému windows a proto ve výchozím nastavení se zobrazí v [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu jako podřízené objekty plochy. V mnoha případech se ale automaticky otevíraná okna jsou logicky podřízené jiný ovládací prvek. Například rozevírací seznam pole se seznamem je logicky podřízené pole se seznamem. Podobně automaticky otevírané okno nabídky jsou logicky podřízený nabídky. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] poskytuje podporu pro Nadřadit automaticky otevíraných oken tak, aby se zdají být podřízené objekty daného přidružený ovládací prvek.  
  
 Chcete-li změnit nadřazenou položku automaticky otevírané okno:  
  
1.  Vytvoření poskytovatele pro překryvné okno. Tento postup vyžaduje, aby třída v automaticky otevíraném okně předem známý.  
  
2.  Implementujte všechny vlastnosti a vzory jako obvykle pro místní, jako by šlo ovládacího prvku v sama o sobě.  
  
3.  Implementace <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.HostRawElementProvider%2A> vlastnost tak, aby se hodnota získaná z <xref:System.Windows.Automation.Provider.AutomationInteropProvider.HostProviderFromHandle%2A>, kde parametr je popisovač okna v automaticky otevíraném okně.  
  
4.  Implementace <xref:System.Windows.Automation.Provider.IRawElementProviderFragment.Navigate%2A> v automaticky otevíraném okně a jeho nadřazený objekt tak, že navigace je zajišťující správné zpracování z logické nadřazené do podřízené logické uzly a mezi podřízené objekty na stejné úrovni.  
  
 Když [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] dojde automaticky otevírané okno, rozpozná, že je přepisována z výchozího navigace a přeskočí v automaticky otevíraném okně vyskytne jako podřízený objekt ploše. Místo toho uzlu se být dostupná jenom prostřednictvím fragment.  
  
 Změna nadřazení není vhodný pro případy, ve kterém ovládací prvek může být hostitelem okno libovolné třídy. Matrici můžete například hostovat jakýkoli typ HWND v jeho pruhy. Řešení těchto případů [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] podporuje alternativní formy přemístění HWND, jak je popsáno v další části.  
  
<a name="Non_WPF_Provider_Repositioning"></a>   
### <a name="non-wpf-provider-repositioning"></a>Umístění poskytovatele bez WPF  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] fragmenty může obsahovat nejmíň dva elementy, které jsou každý obsaženy v okně (HWND). Protože každý HWND má svůj vlastní výchozího zprostředkovatele, který bere v úvahu HWND bude podřízený obsahující HWND, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromové struktury, ve výchozím nastavení, zobrazí HWND ve fragmentu jako podřízené objekty nadřazeného okna. Ve většině případů je to žádoucí chování, ale někdy to může vést k záměně protože neodpovídá logické struktury [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)].  
  
 Dobrým příkladem je ovládacím prvkem matrice. Matrici obsahuje pruhy, z nichž každá pak může obsahovat ovládací prvek na základě HWND například panel nástrojů, do textového pole nebo pole se seznamem. Okno výchozího zprostředkovatele pro matrice HWND vnímá jako podřízené položky ovládacího prvku HWND obsluhy vzdálené správy a poskytovatele matrice vidí pásma jako podřízené objekty. Protože HWND poskytovatele a poskytovatele matrice práci při vytvoření celostní a kombinování jejich podřízené prvky, pásma a ovládací prvky založené na HWND objevit jako podřízené objekty matrice. Logicky ale pouze pásma by se měla zobrazit jako podřízené objekty matrice, a každý vzdálené poskytovatel by měl být vázány na HWND výchozího zprostředkovatele pro ovládací prvek, který obsahuje.  
  
 K tomu zpřístupňuje poskytovateli kořenové fragment matrice sadu podřízené prvky představující pásma. Každé pásmo má jednoho poskytovatele, který může zveřejnit vlastnosti a vzory. Ve své implementaci <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.HostRawElementProvider%2A>, poskytovatel vzdálené vrátí výchozí zprostředkovatel okna pro ovládací prvek HWND, která se získá voláním <xref:System.Windows.Automation.Provider.AutomationInteropProvider.HostProviderFromHandle%2A>a předejte popisovač okna ovládacího prvku. Nakonec implementuje poskytovatele kořenové fragment matrice <xref:System.Windows.Automation.Provider.IRawElementProviderHwndOverride> rozhraní a v jeho provádění <xref:System.Windows.Automation.Provider.IRawElementProviderHwndOverride.GetOverrideProviderForHwnd%2A> vrátí odpovídající obsluhy vzdálené správy zprostředkovatele pro ovládací prvek obsažený v zadané HWND.  
  
## <a name="see-also"></a>Viz také:
- [Přehled zprostředkovatelů automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-providers-overview.md)
- [Vystavení zprostředkovatele automatizace uživatelského rozhraní na straně serveru](../../../docs/framework/ui-automation/expose-a-server-side-ui-automation-provider.md)
- [Vrácení vlastností ze zprostředkovatele automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/return-properties-from-a-ui-automation-provider.md)
- [Vyvolávání událostí ze zprostředkovatele automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/raise-events-from-a-ui-automation-provider.md)
- [Povolení navigace u zprostředkovatele fragmentu automatizace uživatelského rozhraní na straně klienta](../../../docs/framework/ui-automation/enable-navigation-in-a-ui-automation-fragment-provider.md)
- [Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
