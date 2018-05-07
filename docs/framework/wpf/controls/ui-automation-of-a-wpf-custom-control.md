---
title: Automatizace uživatelského rozhraní vlastního ovládacího prvku WPF
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [WPF], applying UI automation
- accessibility [WPF], applying to custom controls
- custom controls [WPF], improving accessibility
- UI Automation [WPF], using with custom controls
ms.assetid: 47b310fc-fbd5-4ce2-a606-22d04c6d4911
ms.openlocfilehash: fbd19591c260b0ad160339b45fd762e7a87bbc74
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="ui-automation-of-a-wpf-custom-control"></a>Automatizace uživatelského rozhraní vlastního ovládacího prvku WPF
[!INCLUDE[TLA#tla_uiautomation](../../../../includes/tlasharptla-uiautomation-md.md)] poskytuje rozhraní jeden, zobecněný této automatizace, které můžou klienti použít k zkontrolujte nebo pracovat uživatelského rozhraní z různých platformy a rozhraní. [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] Umožňuje (testovací) pro zajištění kvality kódu a usnadnění aplikace, jako jsou třeba čtečky obrazovky sloužící ke zkoumání prvky uživatelského rozhraní a simulovat uživatelské interakce s nimi z jiných kódu. Informace o [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] pro všechny platformy, najdete v části usnadnění.  
  
 Toto téma popisuje postupy pro implementaci zprostředkovatele automatizace uživatelského rozhraní na straně serveru pro vlastní ovládací prvek, který spouští v aplikaci WPF. WPF podporuje [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] stromě objekty automatizace partnera, který je paralelní stromu prvky uživatelského rozhraní. Testování kódu a aplikace, které poskytují funkce pro usnadnění přístupu můžete použít sdílené objekty automatizace přímo (pro kódu v procesu) nebo přes rozhraní zobecněný poskytované [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)].  
  
 
  
<a name="AutomationPeerClasses"></a>   
## <a name="automation-peer-classes"></a>Sdílené třídy automatizace  
 WPF ovládací prvky podporu [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] stromě sdílené tříd, které jsou odvozeny od <xref:System.Windows.Automation.Peers.AutomationPeer>. Podle konvence peer třída názvy názvu třídy ovládacího prvku začínat a končit "AutomationPeer". Například <xref:System.Windows.Automation.Peers.ButtonAutomationPeer> je třída sdílené pro <xref:System.Windows.Controls.Button> třídu ovládacího prvku. Jsou přibližně ekvivalentem třídy sdílené [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] řídit typy, ale jsou specifické pro [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] elementy. Automatizace kód, který přistupuje aplikace WPF prostřednictvím [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] rozhraní nepoužívá partnerské uzly automatizace přímo, ale automatizace kódu ve stejném prostoru procesu můžete použít automatizaci partnerské uzly přímo.  
  
<a name="BuiltInAutomationPeerClasses"></a>   
## <a name="built-in-automation-peer-classes"></a>Integrovanou automatizaci pomocí sdílené třídy  
 Elementy implementovat třídu sdílené automatizace, pokud je přijmou rozhraní aktivity od uživatele, nebo obsahují informace potřebné pro uživatele čtečky obrazovky aplikací. Ne všechny WPF vizuální prvky mít automatizace partnerské uzly. Příkladem třídy, které implementují automatizaci partnerské uzly jsou <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.TextBox>, a <xref:System.Windows.Controls.Label>. Příklady tříd, které neimplementují automatizace partnerské uzly jsou třídy, které jsou odvozeny od <xref:System.Windows.Controls.Decorator>, například <xref:System.Windows.Controls.Border>a na základě třídy <xref:System.Windows.Controls.Panel>, jako například <xref:System.Windows.Controls.Grid> a <xref:System.Windows.Controls.Canvas>.  
  
 Základní <xref:System.Windows.Controls.Control> třída nemá odpovídající třídu partnera. Pokud potřebujete tak, aby odpovídaly vlastního ovládacího prvku, která je odvozena od třídy sdílené <xref:System.Windows.Controls.Control>, by měl být odvozen vlastní sdílené třídy z <xref:System.Windows.Automation.Peers.FrameworkElementAutomationPeer>.  
  
<a name="SecurityConsiderations"></a>   
## <a name="security-considerations-for-derived-peers"></a>Důležité informace o zabezpečení pro odvozené partnerské uzly  
 Partnerské uzly automatizace musíte spustit v prostředí s částečným vztahem důvěryhodnosti. Kód v sestavení UIAutomationClient není nakonfigurovaný pro spouštění v prostředí s částečným vztahem důvěryhodnosti a automatizace sdílené kód nesmí odkazovat na této položky assembly. Místo toho používejte třídy v sestavení UIAutomationTypes. Například by měl použít <xref:System.Windows.Automation.AutomationElementIdentifiers> třídy z UIAutomationTypes sestavení, které odpovídá <xref:System.Windows.Automation.AutomationElement> třídy v sestavení UIAutomationClient. Je bezpečné, chcete-li UIAutomationTypes sestavení v kódu sdílené automatizace.  
  
<a name="PeerNavigation"></a>   
## <a name="peer-navigation"></a>Sdílené navigace  
 Po vyhledání sdílené služby automation, kódu v procesu můžete přejít stromu sdílené voláním objektu <xref:System.Windows.Automation.Peers.AutomationPeer.GetChildren%2A> a <xref:System.Windows.Automation.Peers.AutomationPeer.GetParent%2A> metody. Navigace mezi [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] druhé strany implementace podporuje elementů v rámci ovládacího prvku <xref:System.Windows.Automation.Peers.AutomationPeer.GetChildrenCore%2A> metoda. Automatizace uživatelského rozhraní systému volá tuto metodu za účelem sestavení do stromu dílčí prvky obsažené v ovládacím prvku; například seznam položek v seznamu. Výchozí hodnota <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetChildrenCore%2A?displayProperty=nameWithType> metoda prochází vizuální strojové struktuře elementů sestavení stromu automatizace partnerské uzly. Vlastní ovládací prvky přepsat tuto metodu ke zveřejnění podřízené elementy pro klienty automatizace, vrácení partnerské uzly automatizace elementů, které oznamují informace nebo Povolit interakci s uživatelem.  
  
<a name="Customizations"></a>   
## <a name="customizations-in-a-derived-peer"></a>Přizpůsobení v odvozených partnerského uzlu  
 Všechny třídy, které jsou odvozeny od <xref:System.Windows.UIElement> a <xref:System.Windows.ContentElement> obsahovat chráněná virtuální metoda <xref:System.Windows.UIElement.OnCreateAutomationPeer%2A>. WPF volání <xref:System.Windows.UIElement.OnCreateAutomationPeer%2A> GET pro objekt sdílené automatizace pro každý ovládací prvek. Automatizace kódu pomocí partnerským zařízením získat informace o vlastnosti a funkce ovládacího prvku a k simulaci interaktivní použití. Vlastní ovládací prvek, který podporuje automatizaci musí přepsat <xref:System.Windows.UIElement.OnCreateAutomationPeer%2A> a vrátit instanci třídy odvozené z <xref:System.Windows.Automation.Peers.AutomationPeer>. Například, pokud je odvozena z vlastního ovládacího prvku <xref:System.Windows.Controls.Primitives.ButtonBase> třídy a pak pro objekt vrácený rutinou <xref:System.Windows.UIElement.OnCreateAutomationPeer%2A> by měl být odvozen z <xref:System.Windows.Automation.Peers.ButtonBaseAutomationPeer>.  
  
 Při implementaci vlastního ovládacího prvku, je nutné přepsat "Základní" metody ze základní automatizace sdílené třídy, které popisují chování jedinečný a specifické pro vaše vlastní ovládací prvek.  
  
### <a name="override-oncreateautomationpeer"></a>Přepsání OnCreateAutomationPeer  
 Přepsání <xref:System.Windows.UIElement.OnCreateAutomationPeer%2A> metodu pro vaše vlastní ovládací prvek, které se vrátí objekt zprostředkovatele, který musí být přímo nebo nepřímo z <xref:System.Windows.Automation.Peers.AutomationPeer>.  
  
### <a name="override-getpattern"></a>Přepsání GetPattern  
 Partnerské uzly automatizace zjednodušit některé aspekty implementace začlenění na straně serveru [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] poskytovatelů, ale vlastního ovládacího prvku automatizace partnerské uzly musí stále zpracování vzor rozhraní. Jako-grafického subsystému WPF poskytovatelů, partnerské uzly podpora vzorů ovládacích prvků tím, že poskytuje implementace rozhraní <xref:System.Windows.Automation.Provider?displayProperty=nameWithType> obor názvů, jako například <xref:System.Windows.Automation.Provider.IInvokeProvider>. Rozhraní pro vzor řízení se dá implementovat partnerem sám sebe nebo jiný objekt. Implementace druhé strany <xref:System.Windows.Automation.Peers.AutomationPeer.GetPattern%2A> vrátí objekt, který podporuje zadanému vzoru. [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] volání kódu <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetPattern%2A> metoda a určuje <xref:System.Windows.Automation.Peers.PatternInterface> hodnota výčtu. Přepsání z <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetPattern%2A> by měla vrátit objekt, který implementuje zadanému vzoru. Pokud vlastní ovládací prvek nemá vlastní implementaci vzor, můžete volat základní typ provádění <xref:System.Windows.Automation.Peers.AutomationPeer.GetPattern%2A> načíst jeho implementace nebo hodnota null, pokud vzor není podporovaná pro tento typ ovládacího prvku. Například vlastního ovládacího prvku NumericUpDown lze nastavit na hodnotu v rozsahu, takže jeho [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] by implementovat sdílené <xref:System.Windows.Automation.Provider.IRangeValueProvider> rozhraní. Následující příklad ukazuje způsob druhé strany <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetPattern%2A> je metoda potlačena za účelem reagovat na <xref:System.Windows.Automation.Peers.PatternInterface.RangeValue?displayProperty=nameWithType> hodnotu.  
  
 [!code-csharp[CustomControlNumericUpDown#GetPattern](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp/CustomControlLibrary/NumericUpDown.cs#getpattern)]
 [!code-vb[CustomControlNumericUpDown#GetPattern](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic/customcontrollibrary/numericupdown.vb#getpattern)]  
  
 A <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetPattern%2A> metoda můžete také zadat dílčí prvek jako zprostředkovatel vzor. Následující kód ukazuje, jak <xref:System.Windows.Controls.ItemsControl> přenosy posuňte vzor zpracování na druhé straně jeho vnitřní <xref:System.Windows.Controls.ScrollViewer> ovládacího prvku.  
  
```csharp  
public override object GetPattern(PatternInterface patternInterface)  
{  
    if (patternInterface == PatternInterface.Scroll)  
    {  
        ItemsControl owner = (ItemsControl) base.Owner;  
  
        // ScrollHost is internal to the ItemsControl class  
        if (owner.ScrollHost != null)  
        {  
            AutomationPeer peer = UIElementAutomationPeer.CreatePeerForElement(owner.ScrollHost);  
            if ((peer != null) && (peer is IScrollProvider))  
            {  
                peer.EventsSource = this;  
                return (IScrollProvider) peer;  
            }  
        }  
    }  
    return base.GetPattern(patternInterface);  
}  
```  
  
```vb  
Public Class Class1  
    Public Overrides Function GetPattern(ByVal patternInterface__1 As PatternInterface) As Object  
        If patternInterface1 = PatternInterface.Scroll Then  
            Dim owner As ItemsControl = DirectCast(MyBase.Owner, ItemsControl)  
  
            ' ScrollHost is internal to the ItemsControl class  
            If owner.ScrollHost IsNot Nothing Then  
                Dim peer As AutomationPeer = UIElementAutomationPeer.CreatePeerForElement(owner.ScrollHost)  
                If (peer IsNot Nothing) AndAlso (TypeOf peer Is IScrollProvider) Then  
                    peer.EventsSource = Me  
                    Return DirectCast(peer, IScrollProvider)  
                End If  
            End If  
        End If  
        Return MyBase.GetPattern(patternInterface1)  
    End Function  
End Class  
```  
  
 Pokud chcete zadat dílčí element pro zpracování vzor, tento kód získá objekt dílčí element, vytvoří partnerského uzlu pomocí <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.CreatePeerForElement%2A> Nastaví metodu, <xref:System.Windows.Automation.Peers.AutomationPeer.EventsSource%2A> vlastnost nové partnerského uzlu na aktuální partnera a vrátí nové sdílené. Nastavení <xref:System.Windows.Automation.Peers.AutomationPeer.EventsSource%2A> na dílčí prvek bránil dílčí prvek ve stromu automatizace sdílené a označí všechny události vyvolané službou dílčí prvek jako pocházející z ovládacího prvku zadaná v <xref:System.Windows.Automation.Peers.AutomationPeer.EventsSource%2A>. <xref:System.Windows.Controls.ScrollViewer> Řízení nezobrazí ve stromu automatizace a posouvání události, které generuje se zobrazí z <xref:System.Windows.Controls.ItemsControl> objektu.  
  
### <a name="override-core-methods"></a>Přepsání metody "Základní"  
 Automatizace kód získá informace o vaší kontrole voláním veřejné metody třídy partnera. Zadání informací o vaší kontrole, potlačí každá metoda, jejíž název končí řetězcem "Základní" při implementaci ovládacího prvku se liší od poskytnutá třídě sdílené základní automatizace. Minimálně musí implementovat vlastní ovládací prvek <xref:System.Windows.Automation.Peers.AutomationPeer.GetClassNameCore%2A> a <xref:System.Windows.Automation.Peers.AutomationPeer.GetAutomationControlTypeCore%2A> metod, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[CustomControlNumericUpDown#CoreOverrides](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp/CustomControlLibrary/NumericUpDown.cs#coreoverrides)]
 [!code-vb[CustomControlNumericUpDown#CoreOverrides](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic/customcontrollibrary/numericupdown.vb#coreoverrides)]  
  
 Vaši implementaci <xref:System.Windows.Automation.Peers.AutomationPeer.GetAutomationControlTypeCore%2A> popisuje kontrolu nad vrácením <xref:System.Windows.Automation.ControlType> hodnotu. I když můžete vrátit <xref:System.Windows.Automation.ControlType.Custom?displayProperty=nameWithType>, jeden další specifické typy ovládacích prvků by měla vrátit, pokud přesně popisuje vlastního ovládacího prvku. Vrácená hodnota <xref:System.Windows.Automation.ControlType.Custom?displayProperty=nameWithType> vyžaduje další práci pro zprostředkovatele implementovat [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)], a [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] klienta produkty nedaří předvídat řízení strukturu, interakce klávesnice a vzory možné ovládacích prvků.  
  
 Implementace <xref:System.Windows.Automation.Peers.AutomationPeer.IsContentElementCore%2A> a <xref:System.Windows.Automation.Peers.AutomationPeer.IsControlElementCore%2A> metod udávající, zda vlastní ovládací prvek obsahuje data obsah nebo plnit roli interaktivní uživatelské rozhraní (nebo obě). Ve výchozím nastavení, obě metody vrátit `true`. Tato nastavení zlepšují použitelnost automatizace nástrojů, jako jsou třeba čtečky obrazovky, které mohou použít tyto metody pro filtrování strom automatizace. Pokud vaše <xref:System.Windows.Automation.Peers.AutomationPeer.GetPattern%2A> vzor přenosy metoda zpracování na partnera dílčí element, sdílené dílčí element <xref:System.Windows.Automation.Peers.AutomationPeer.IsControlElementCore%2A> metoda může vrátit hodnotu false, aby Skrýt dílčí element sdílené ze stromu automatizace. Například posouvání <xref:System.Windows.Controls.ListBox> se zpracovává souborem <xref:System.Windows.Controls.ScrollViewer>a druhá automatizace pro <xref:System.Windows.Automation.Peers.PatternInterface.Scroll?displayProperty=nameWithType> je vrácen rutinou <xref:System.Windows.Automation.Peers.AutomationPeer.GetPattern%2A> metodu <xref:System.Windows.Automation.Peers.ScrollViewerAutomationPeer> přidružená <xref:System.Windows.Automation.Peers.ListBoxAutomationPeer>. Proto <xref:System.Windows.Automation.Peers.AutomationPeer.IsControlElementCore%2A> metodu <xref:System.Windows.Automation.Peers.ScrollViewerAutomationPeer> vrátí `false`tak, aby <xref:System.Windows.Automation.Peers.ScrollViewerAutomationPeer> nezobrazí ve stromu automatizace.  
  
 Vaše sdílené automatizace by měl poskytovat příslušných výchozích hodnot pro vlastní ovládací prvek. Všimněte si, že XAML, který odkazuje na vlastní ovládací prvek můžete přepsat vaší implementace sdílené základní metody zahrnutím <xref:System.Windows.Automation.AutomationProperties> atributy. Například následující XAML vytvoří tlačítko, které má dva přizpůsobit [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] vlastnosti.  
  
```xaml  
<Button AutomationProperties.Name="Special"   
    AutomationProperties.HelpText="This is a special button."/>  
```  
  
### <a name="implement-pattern-providers"></a>Implementace vzoru zprostředkovatele  
 Rozhraní implementované vlastního zprostředkovatele jsou explicitně deklarované, pokud je element vlastnící odvozena přímo z <xref:System.Windows.Controls.Control>. Například následující kód deklaruje partnerské zařízení pro <xref:System.Windows.Controls.Control> hodnotu rozsahu, která implementuje.  
  
```csharp  
public class RangePeer1 : FrameworkElementAutomationPeer, IRangeValueProvider { }  
```  
  
```vb  
Public Class RangePeer1  
    Inherits FrameworkElementAutomationPeer  
    Implements IRangeValueProvider  
End Class  
```  
  
 Pokud je vlastnícím ovládací prvek odvozen z konkrétního typu ovládacího prvku, jako <xref:System.Windows.Controls.Primitives.RangeBase>, partnerský uzel může být odvozen z ekvivalentní sdílené odvozené třídy. V takovém případě by partnerem odvozena od <xref:System.Windows.Automation.Peers.RangeBaseAutomationPeer>, která poskytuje základní implementaci <xref:System.Windows.Automation.Provider.IRangeValueProvider>. Následující kód ukazuje deklaraci partnerského uzlu.  
  
```csharp  
public class RangePeer2 : RangeBaseAutomationPeer { }  
```  
  
```vb  
Public Class RangePeer2  
    Inherits RangeBaseAutomationPeer  
End Class  
```  
  
 Příklad implementace, najdete v části [vlastní NumericUpDown – ovládací prvek s motiv a ukázkové podpora automatizace uživatelského rozhraní](http://go.microsoft.com/fwlink/?LinkID=160025).  
  
### <a name="raise-events"></a>Vyvolávání událostí  
 Klienti automatizace může přihlásit k událostí automatizace. Vlastní ovládací prvky musí nahlásit změny k řízení stavu voláním <xref:System.Windows.Automation.Peers.AutomationPeer.RaiseAutomationEvent%2A> metoda. Podobně když se změní hodnota vlastnosti, volání <xref:System.Windows.Automation.Peers.AutomationPeer.RaisePropertyChangedEvent%2A> metoda. Následující kód ukazuje, jak získat objekt sdílené z v rámci řídicí kód a volání metody vyvolat událost. Jako optimalizace Určuje kód, pokud jsou všechny moduly pro naslouchání pro tento typ události. Vyvolá událost jenom v případě, že jsou naslouchací procesy zabraňuje zbytečným režijní náklady a pomáhá ovládacího prvku zůstanou reaguje.  
  
 [!code-csharp[CustomControlNumericUpDown#RaiseEventFromControl](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp/CustomControlLibrary/NumericUpDown.cs#raiseeventfromcontrol)]
 [!code-vb[CustomControlNumericUpDown#RaiseEventFromControl](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic/customcontrollibrary/numericupdown.vb#raiseeventfromcontrol)]  
  
## <a name="see-also"></a>Viz také  
 [Přehled automatizace uživatelského rozhraní](../../../../docs/framework/ui-automation/ui-automation-overview.md)  
 [NumericUpDown vlastní ovládací prvek s motiv a ukázkové podpora automatizace uživatelského rozhraní](http://go.microsoft.com/fwlink/?LinkID=160025)  
 [Implementace zprostředkovatele automatizace uživatelského rozhraní na straně serveru](../../../../docs/framework/ui-automation/server-side-ui-automation-provider-implementation.md)
