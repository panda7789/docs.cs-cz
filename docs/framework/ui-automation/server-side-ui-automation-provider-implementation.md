---
title: "Implementace zprostředkovatele automatizace uživatelského rozhraní na straně serveru"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- server-side UI Automation provider implementation
- UI Automation, server-side provider implementation
- provider implementation, UI Automation
ms.assetid: 6acc6d08-bd67-4e2e-915c-9c1d34eb86fe
caps.latest.revision: "39"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 03ebb5a8193d3376d40fa830f13ab9324846ba2c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="server-side-ui-automation-provider-implementation"></a>Implementace zprostředkovatele automatizace uživatelského rozhraní na straně serveru
> [!NOTE]
>  Tato dokumentace je určena pro rozhraní .NET Framework vývojáře, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], najdete v části [rozhraní API systému Windows automatizace: automatizace uživatelského rozhraní](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Tato část popisuje postupy pro implementaci zprostředkovatele automatizace uživatelského rozhraní na straně serveru pro vlastní ovládací prvek.  
  
 Implementace pro [!INCLUDE[TLA#tla_wpf](../../../includes/tlasharptla-wpf-md.md)] elementy a jiných-[!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] elementy (jsou určené pro [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)]) se podstatně liší. [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]elementy poskytují podporu pro [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] prostřednictvím třídy odvozené od <xref:System.Windows.Automation.Peers.AutomationPeer>. Jinou hodnotu než[!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] elementy poskytovat podporu prostřednictvím implementace rozhraní poskytovatele.  
  
<a name="Security_Considerations"></a>   
## <a name="security-considerations"></a>Důležité informace o zabezpečení  
 Zprostředkovatelé zasílány mohli pracovat v prostředí s částečným vztahem důvěryhodnosti. Protože UIAutomationClient.dll není nakonfigurována pro spuštění v částečné důvěryhodnosti, zprostředkovatele kódu nesmí odkazovat na této položky assembly. Pokud k tomu, aby kód může spustit v prostředí plné důvěryhodnosti, ale pak selhání v prostředí s částečným vztahem důvěryhodnosti.  
  
 Nepoužívejte na konkrétní pole z třídy v UIAutomationClient.dll například v <xref:System.Windows.Automation.AutomationElement>. Místo toho použijte ekvivalentní pole z třídy v UIAutomationTypes.dll, jako například <xref:System.Windows.Automation.AutomationElementIdentifiers>.  
  
<a name="Provider_Implementation_by_WPF_Elements"></a>   
## <a name="provider-implementation-by-windows-presentation-foundation-elements"></a>Implementace zprostředkovatele Windows Presentation Foundation elementy  
 Další informace v tomto tématu najdete v tématu [automatizace uživatelského rozhraní ovládacího prvku WPF vlastní](../../../docs/framework/wpf/controls/ui-automation-of-a-wpf-custom-control.md).  
  
<a name="Provider_Implementation_by_non_WPF_Elements"></a>   
## <a name="provider-implementation-by-non-wpf-elements"></a>Implementace zprostředkovatele pomocí grafického subsystému WPF elementy  
 Vlastní ovládací prvky, které nejsou součástí jsou [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] framework, ale které jsou zapsané ve spravovaném kódu (většinou jsou to [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] ovládací prvky), poskytují podporu pro [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] implementací rozhraní. Každý element musí implementovat alespoň jeden z rozhraní uvedená v první tabulce v další části. Kromě toho pokud element podporuje jeden nebo více vzorů ovládacích prvků, musí implementovat rozhraní vhodné pro každý – vzor ovládacích prvků.  
  
 Vaše [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] projektu zprostředkovatele musí odkazovat na následující sestavení:  
  
-   UIAutomationProviders.dll  
  
-   UIAutomationTypes.dll  
  
-   Knihovně WindowsBase.dll  
  
  
<a name="Provider_Interfaces"></a>   
### <a name="provider-interfaces"></a>Zprostředkovatel rozhraní  
 Každý [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] poskytovatel musí implementovat jednu z následujících rozhraní.  
  
|Rozhraní|Popis|  
|---------------|-----------------|  
|<xref:System.Windows.Automation.Provider.IRawElementProviderSimple>|Poskytuje funkce pro jednoduché ovládací prvek hostované v okně, včetně podpory pro vzory ovládacích prvků a vlastností.|  
|<xref:System.Windows.Automation.Provider.IRawElementProviderFragment>|Dědí z <xref:System.Windows.Automation.Provider.IRawElementProviderSimple>. Přidá funkce pro nějaký element v ovládacím prvku složité, včetně navigace v rámci fragment, nastavení fokusu a vrácení ohraničující obdélník elementu.|  
|<xref:System.Windows.Automation.Provider.IRawElementProviderFragmentRoot>|Dědí z <xref:System.Windows.Automation.Provider.IRawElementProviderFragment>. Přidá funkce pro kořenový element v prvku složité, včetně vyhledání podřízený element v zadaných souřadnic a nastavení stavu fokus pro celý ovládací prvek.|  
  
 Následující rozhraní poskytují další funkce, ale nejsou nutné k implementaci.  
  
|Rozhraní|Popis|  
|---------------|-----------------|  
|<xref:System.Windows.Automation.Provider.IRawElementProviderAdviseEvents>|Povolí zprostředkovatele pro sledování požadavků pro události.|  
|<xref:System.Windows.Automation.Provider.IRawElementProviderHwndOverride>|Umožňuje přemístění systémem Windows elementů v rámci [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu fragment.|  
  
 Všechna rozhraní v <xref:System.Windows.Automation.Provider> obor názvů jsou pro podporu řízení vzor.  
  
<a name="Requirements_for_Non_WPF_Providers"></a>   
### <a name="requirements-for-non-wpf-providers"></a>Požadavky pro zprostředkovatele grafického subsystému WPF  
 Chcete-li komunikovat s [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], vlastní ovládací prvek musí implementovat následující hlavní oblasti funkcí:  
  
|Funkce|Implementace|  
|-------------------|--------------------|  
|Vystavení zprostředkovatele, který se[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|V reakci na WM_GETOBJECT zprávy odeslané do okna Ovládací prvek, vrátí objekt, který implementuje <xref:System.Windows.Automation.Provider.IRawElementProviderSimple> (nebo odvozené rozhraní). Pro fragmenty musí se jednat zprostředkovatele pro kořenovou fragment.|  
|Zadejte hodnoty vlastností|Implementace <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPropertyValue%2A> k poskytování nebo hodnoty přepsání.|  
|Povolit klientům komunikovat pomocí ovládacího prvku|Implementace rozhraní, které podporují vzory ovládacích prvků, jako například <xref:System.Windows.Automation.Provider.IInvokeProvider>. Vrátí tyto zprostředkovatele vzor ve vaši implementaci <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A>.|  
|Vyvolávání událostí|Volání jednoho z statických metod <xref:System.Windows.Automation.Provider.AutomationInteropProvider> vyvolat událost, který může klient naslouchat.|  
|Povolení navigace a zaměřením v rámci fragment|Implementace <xref:System.Windows.Automation.Provider.IRawElementProviderFragment> pro každý prvek v rámci fragment. (Není potřeba pro prvky, které nejsou součástí fragment.)|  
|Povolit zaměření a umístění podřízený element v fragment|Implementace <xref:System.Windows.Automation.Provider.IRawElementProviderFragmentRoot>. (Není potřeba pro prvky, které není fragmentovat kořeny.)|  
  
<a name="Property_Values_in_Non_WPF_Providers"></a>   
### <a name="property-values-in-non-wpf-providers"></a>Hodnoty vlastností ve zprostředkovatelích grafického subsystému WPF  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]zprostředkovatelé pro vlastní ovládací prvky musí podporovat některé vlastnosti, které lze použít systém automatizace a klientské aplikace. U elementů, které jsou hostované v systému windows (HWND) [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] můžete načíst některé vlastnosti od výchozího zprostředkovatele okno, ale ostatní musí získat z vlastního zprostředkovatele.  
  
 Zprostředkovatelé pro ovládací prvky HWND na základě nemusíte obvykle zadejte následující vlastnosti (identifikovaný hodnoty polí):  
  
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
>  <xref:System.Windows.Automation.AutomationElementIdentifiers.RuntimeIdProperty> Jednoduché elementu nebo fragmentu kořenové hostované v okně se získávají z okna; však fragment prvky pod kořenovým adresářem (například seznam položek v seznamu), musíte zadat své vlastní identifikátory. Další informace naleznete v tématu <xref:System.Windows.Automation.Provider.IRawElementProviderFragment.GetRuntimeId%2A>.  
>   
>  <xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty> Má být vrácen pro zprostředkovatele hostované v [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] ovládacího prvku. V takovém případě může být výchozí zprostředkovatel okno se nepodařilo načíst správnou hodnotu.  
>   
>  <xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty> Je obvykle dodávaných poskytovatelem hostitele. Například, pokud vlastní ovládací prvek je odvozený od <xref:System.Windows.Forms.Control>, název je odvozený od `Text` vlastností ovládacího prvku.  
  
 Příklad kódu, najdete v části [vrátit vlastností ze zprostředkovatele automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/return-properties-from-a-ui-automation-provider.md).  
  
<a name="Events_in_Non_WPF_Providers"></a>   
### <a name="events-in-non-wpf-providers"></a>Události ve zprostředkovatelích grafického subsystému WPF  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Zprostředkovatelé by měla vyvolat události oznámení klientských aplikací změny ve stavu uživatelského rozhraní. Následující metody se používají k vyvolávání událostí.  
  
|Metoda|Popis|  
|------------|-----------------|  
|<xref:System.Windows.Automation.Provider.AutomationInteropProvider.RaiseAutomationEvent%2A>|Vyvolá různé události, včetně události aktivované vzory ovládacích prvků.|  
|<xref:System.Windows.Automation.Provider.AutomationInteropProvider.RaiseAutomationPropertyChangedEvent%2A>|Vyvolá událost, když [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] došlo ke změně vlastností.|  
|<xref:System.Windows.Automation.Provider.AutomationInteropProvider.RaiseStructureChangedEvent%2A>|Vyvolá událost při strukturu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu došlo ke změně; například podle odebrání nebo přidání elementu.|  
  
 Účelem událost je o upozornění klienta o něco probíhající [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)], zda je aktivován aktivity [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] samotného systému. Například událost identifikovaný <xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent> by měla být zvýšena při každém vyvolání ovládacího prvku buď prostřednictvím přímé uživatelský vstup, nebo volání aplikace klienta <xref:System.Windows.Automation.InvokePattern.Invoke%2A>.  
  
 Za účelem optimalizace výkonu, můžete poskytovatele selektivně vyvolávání událostí, nebo vůbec vyvolat žádné události. Pokud žádná aplikace klienta je zaregistrován k jejich odběru. Následující metody se používají pro optimalizaci.  
  
|Metoda|Popis|  
|------------|-----------------|  
|<xref:System.Windows.Automation.Provider.AutomationInteropProvider.ClientsAreListening%2A>|Tato statická vlastnost určuje, zda mají všechny klientské aplikace předplatné [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] události.|  
|<xref:System.Windows.Automation.Provider.IRawElementProviderAdviseEvents>|Poskytovatele implementace tohoto rozhraní v kořenovém adresáři fragment umožní, aby se doporučuje, když se klienti zaregistrovat a zrušit registraci obslužné rutiny události pro události na fragment.|  
  
<a name="Non_WPF_Provider_Navigation"></a>   
### <a name="non-wpf-provider-navigation"></a>Navigace zprostředkovatele-grafického subsystému WPF  
 Zprostředkovatelé pro jednoduché ovládací prvky, jako je například vlastní tlačítko hostované v okně (HWND) nemusí podporovat navigace v rámci [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu. Navigace do a z elementu se zpracovává souborem výchozího zprostředkovatele pro okno hostitele, který je určený implementace <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.HostRawElementProvider%2A>. Při implementaci zprostředkovatele pro komplexní vlastního ovládacího prvku, ale musí podporovat navigace mezi kořenového uzlu fragmentu a jeho následníky a mezi uzly na stejné úrovni.  
  
> [!NOTE]
>  Elementy fragment, než je kořenový adresář musí vracet `null` odkazovat z <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.HostRawElementProvider%2A>, protože nejsou přímo hostované v okně a žádný výchozí zprostředkovatel může podporovat navigace do a z nich.  
  
 Struktura fragment je dáno vaši implementaci <xref:System.Windows.Automation.Provider.IRawElementProviderFragment.Navigate%2A>. Pro všechny možné směry z každé fragment tato metoda vrátí objekt zprostředkovatele pro element v tomto směru. Pokud je v tomto směru žádné elementy, vrátí metoda `null` odkaz.  
  
 Fragment kořenové podporuje navigační pouze pro podřízené elementy. Například vrátí pole se seznamem první položku v seznamu Pokud je směr <xref:System.Windows.Automation.Provider.NavigateDirection.FirstChild>a pokud je směr poslední položky <xref:System.Windows.Automation.Provider.NavigateDirection.LastChild>. Fragment kořenové nepodporuje navigace k nadřazené nebo na stejné úrovni; To se zpracovává souborem zprostředkovatele okno hostitele.  
  
 Elementy fragment, které nejsou kořenu musí podporovat navigace pro nadřazenou a všechny položky na stejné úrovni a podřízené objekty, které mají.  
  
<a name="Non_WPF_Provider_Reparenting"></a>   
### <a name="non-wpf-provider-reparenting"></a>Reparenting zprostředkovatele grafického subsystému WPF  
 Automaticky otevíraná okna jsou ve skutečnosti nejvyšší úrovně windows a to znamená ve výchozím nastavení se zobrazí v [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu jako podřízené objekty plochy. V mnoha případech automaticky otevíraná okna jsou však logicky podřízené některé jiné ovládacímu prvku. Rozevírací seznam pole se seznamem je například logicky Podřízená pole se seznamem. Podobně kontextovou nabídku je logicky podřízenou v nabídce. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]poskytuje podporu pro Nadřadit automaticky otevíraná okna tak, aby se zobrazí jako podřízené objekty přidruženého ovládacího prvku.  
  
 Chcete-li Nadřadit automaticky otevírané okno:  
  
1.  Vytvoření poskytovatele pro překryvné okno. To vyžaduje, aby je předem známo třídu překryvné okno.  
  
2.  Implementujte všechny vlastnosti a vzory jako obvykle pro tento automaticky otevírané okno, jako by šlo ovládacího prvku v jeho vlastní práva.  
  
3.  Implementace <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.HostRawElementProvider%2A> vlastnosti, které se vrátí hodnotu získané z <xref:System.Windows.Automation.Provider.AutomationInteropProvider.HostProviderFromHandle%2A>, kde parametr je popisovač okna překryvné okno.  
  
4.  Implementace <xref:System.Windows.Automation.Provider.IRawElementProviderFragment.Navigate%2A> pro překryvné okno a jeho nadřazený objekt tak, že navigace je správné zpracování z logické nadřazeného logické podřízených objektů a mezi podřízené objekty na stejné úrovni.  
  
 Při [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zaznamená místním okně, jeho rozpozná, že navigační přepíšou z výchozího a přeskočí v místním okně při jeho zjištění jako podřízenou plochy. Místo toho uzlu pouze bude dostupný prostřednictvím fragment.  
  
 Reparenting není vhodný pro případy, kde ovládacího prvku může hostovat okno libovolné třídy. Například matrice může hostovat libovolného typu HWND v jeho pásma. Chcete-li tyto případy zpracují [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] podporuje alternativní forma HWND přemístění, jak je popsáno v následující části.  
  
<a name="Non_WPF_Provider_Repositioning"></a>   
### <a name="non-wpf-provider-repositioning"></a>Zprostředkovatel grafického subsystému WPF přemístění  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]fragmenty může obsahovat minimálně dva elementy, které jsou všechny obsažené v okně (HWND). Protože každý HWND má svou vlastní výchozího zprostředkovatele, který zvažuje HWND jako podřízenou obsahující HWND, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu, ve výchozím nastavení, zobrazí HWND ve fragmentu jako podřízené objekty nadřazeného okna. Ve většině případů to je žádoucí chování, ale v některých případech může vést k záměně protože neodpovídá logické struktury [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)].  
  
 Dobrým příkladem tohoto objektu je ovládacím prvkem matrice. Matrice obsahuje pruhy, z nichž každá pak může obsahovat ovládacího prvku na základě HWND například panel nástrojů, textové pole nebo pole se seznamem. Okno výchozího zprostředkovatele pro matrice HWND vidí vzdálené řízení HWND jako podřízené objekty a poskytovateli matrice uvidí pásma jako podřízené objekty. Vzhledem k poskytovateli HWND a poskytovateli matrice jsou práci současně a kombinování jejich podřízené, pásma a ovládací prvky založené na HWND zobrazí jako podřízené objekty matrice. Logicky ale pouze pásma mají zobrazit jako podřízené objekty matrice a každý zprostředkovatele pro vzdálenou správu by měla kombinaci s HWND výchozího zprostředkovatele pro ovládací prvek, který obsahuje.  
  
 K tomu, zprostředkovatel kořenové fragment pro matrice poskytuje sadu představující pásma podřízené objekty. Každé vzdálené nemá jednoho poskytovatele, který může odhalit vlastnosti a vzory. Při implementaci <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.HostRawElementProvider%2A>, vrátí výchozí zprostředkovatel okna pro ovládací prvek HWND, které získá voláním zprostředkovatele pro vzdálenou správu <xref:System.Windows.Automation.Provider.AutomationInteropProvider.HostProviderFromHandle%2A>a předejte popisovač okna ovládacího prvku. Nakonec kořenové zprostředkovatele fragmentu pro matrice implementuje <xref:System.Windows.Automation.Provider.IRawElementProviderHwndOverride> rozhraní a v jeho implementaci <xref:System.Windows.Automation.Provider.IRawElementProviderHwndOverride.GetOverrideProviderForHwnd%2A> vrátí zprostředkovatele odpovídající vzdálenou správu pro ovládací prvek obsažené v zadané HWND.  
  
## <a name="see-also"></a>Viz také  
 [Přehled zprostředkovatelů automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-providers-overview.md)  
 [Vystavení zprostředkovatele automatizace uživatelského rozhraní na straně serveru](../../../docs/framework/ui-automation/expose-a-server-side-ui-automation-provider.md)  
 [Vrácení vlastností ze zprostředkovatele automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/return-properties-from-a-ui-automation-provider.md)  
 [Vyvolávání událostí ze zprostředkovatele automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/raise-events-from-a-ui-automation-provider.md)  
 [Povolení navigace u zprostředkovatele fragmentu automatizace uživatelského rozhraní na straně klienta](../../../docs/framework/ui-automation/enable-navigation-in-a-ui-automation-fragment-provider.md)  
 [Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [Ukázka jednoduchého zprostředkovatele](http://msdn.microsoft.com/en-us/c10a6255-e8dc-494b-a051-15111b47984a)  
 [Ukázka zprostředkovatele fragmentu](http://msdn.microsoft.com/en-us/778ef1bc-8610-4bc9-886e-aeff94a8a13e)
