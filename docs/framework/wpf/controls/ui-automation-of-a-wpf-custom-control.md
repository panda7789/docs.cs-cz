---
title: Automatizace uživatelského rozhraní vlastního ovládacího prvku
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
ms.openlocfilehash: 97db94215220ac2a68e0395bd63b7a874a745a48
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/13/2020
ms.locfileid: "81243242"
---
# <a name="ui-automation-of-a-wpf-custom-control"></a>Automatizace uživatelského rozhraní vlastního ovládacího prvku WPF
[!INCLUDE[TLA#tla_uiautomation](../../../../includes/tlasharptla-uiautomation-md.md)]poskytuje jediné, generalizované rozhraní, které mohou klienti automatizace použít ke kontrole nebo provozu uživatelských rozhraní různých platforem a architektur. [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)]umožňuje kódu zajištění kvality (testování) a aplikacím pro usnadnění přístupu, jako jsou programy pro čtení z obrazovky, prozkoumat prvky uživatelského rozhraní a simulovat interakci uživatele s nimi z jiného kódu. Informace o [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] všech platformách najdete v tématu Usnadnění přístupu.  
  
 Toto téma popisuje, jak implementovat zprostředkovatele automatizace uživatelského rozhraní na straně serveru pro vlastní ovládací prvek, který běží v aplikaci WPF. WPF [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] podporuje prostřednictvím stromu peer automatizace objektů, které paralely stromu prvků uživatelského rozhraní. Testovací kód a aplikace, které poskytují funkce usnadnění, mohou používat objekty partnerského typu [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)]automatizace přímo (pro kód v procesu) nebo prostřednictvím zobecněné rozhraní poskytované aplikací .  

<a name="AutomationPeerClasses"></a>
## <a name="automation-peer-classes"></a>Třídy partnerského partnera automatizace  
 WPF řídí [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] podporu prostřednictvím stromu <xref:System.Windows.Automation.Peers.AutomationPeer>peer tříd, které jsou odvozeny z . Podle konvence, peer třídy názvy začínají název třídy ovládacího prvku a končí "AutomationPeer". Například <xref:System.Windows.Automation.Peers.ButtonAutomationPeer> je třída peer <xref:System.Windows.Controls.Button> pro třídu ovládacího prvku. Třídy rovnocenných počítačů [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] jsou zhruba ekvivalentní typům ovládacích prvků, ale jsou specifické pro prvky WPF. Automatizační kód, který přistupuje k aplikacím WPF prostřednictvím [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] rozhraní, nepoužívá přímo partnery automatizace, ale kód automatizace ve stejném prostoru procesu může přímo používat partnery automatizace.  
  
<a name="BuiltInAutomationPeerClasses"></a>
## <a name="built-in-automation-peer-classes"></a>Vestavěné třídy rovnocenných účastnik automatizace  
 Elementy implementovat třídu peer automatizace, pokud přijímají aktivitu rozhraní od uživatele nebo pokud obsahují informace potřebné pro uživatele aplikací pro čtení z obrazovky. Ne všechny vizuální prvky WPF mají partnery automatizace. Příklady tříd, které implementují partnerské společnosti automatizace <xref:System.Windows.Controls.Button>jsou , <xref:System.Windows.Controls.TextBox>a <xref:System.Windows.Controls.Label>. Příklady tříd, které neimplementují partnerské <xref:System.Windows.Controls.Decorator>strany <xref:System.Windows.Controls.Border>automatizace, <xref:System.Windows.Controls.Panel>jsou třídy, které jsou odvozeny z , například , a třídy založené na , například <xref:System.Windows.Controls.Grid> a <xref:System.Windows.Controls.Canvas>.  
  
 Základní <xref:System.Windows.Controls.Control> třída nemá odpovídající peer třídy. Pokud potřebujete třídu partnera, která bude odpovídat <xref:System.Windows.Controls.Control>vlastnímu ovládacímu prvku, <xref:System.Windows.Automation.Peers.FrameworkElementAutomationPeer>který je odvozen z , měli byste odvodit vlastní třídu rovnocenných společností z .  
  
<a name="SecurityConsiderations"></a>
## <a name="security-considerations-for-derived-peers"></a>Důležité informace o zabezpečení pro odvozené partnery  
 Partneři automatizace musí být spuštěni v prostředí s částečnou důvěryhodností. Kód v sestavení UIAutomationClient není nakonfigurován tak, aby byl spuštěn v prostředí s částečnou důvěryhodností, a kód partnerského typu automatizace by neměl odkazovat na toto sestavení. Místo toho byste měli použít třídy v sestavení UIAutomationTypes. Například byste měli <xref:System.Windows.Automation.AutomationElementIdentifiers> použít třídu z sestavení UIAutomationTypes, <xref:System.Windows.Automation.AutomationElement> která odpovídá třídě v sestavení UIAutomationClient. Je bezpečné odkazovat na sestavení UIAutomationTypes v kódu partnerského typu automatizace.  
  
<a name="PeerNavigation"></a>
## <a name="peer-navigation"></a>Navigace mezi dvěma účastníky  
 Po vyhledání partnera automatizace může vprocesový kód procházet strom <xref:System.Windows.Automation.Peers.AutomationPeer.GetChildren%2A> <xref:System.Windows.Automation.Peers.AutomationPeer.GetParent%2A> u druhé strany voláním objektu a metod. Navigace mezi wpf prvky v rámci ovládacího prvku <xref:System.Windows.Automation.Peers.AutomationPeer.GetChildrenCore%2A> je podporován a peer implementace metody. Systém automatizace uživatelského rozhraní volá tuto metodu k vytvoření stromu podelementů obsažených v ovládacím prvku; například seznam položek v seznamu. Výchozí <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetChildrenCore%2A?displayProperty=nameWithType> metoda prochází vizuální strom prvků k vytvoření stromu automatizace partnerů. Vlastní ovládací prvky přepsat tuto metodu vystavit podřízené prvky automatizace klientům, vrácení automatizace partnerské prvky, které přenášejí informace nebo umožňují interakci s uživatelem.  
  
<a name="Customizations"></a>
## <a name="customizations-in-a-derived-peer"></a>Vlastní nastavení v odvozeném partnerské mitku  
 Všechny třídy, <xref:System.Windows.UIElement> <xref:System.Windows.ContentElement> které jsou odvozeny a obsahují chráněnou virtuální metodu <xref:System.Windows.UIElement.OnCreateAutomationPeer%2A>. WPF <xref:System.Windows.UIElement.OnCreateAutomationPeer%2A> volání získat peer objekt automatizace pro každý ovládací prvek. Automatizační kód můžete použít peer získat informace o vlastnostech a funkcích ovládacího prvku a simulovat interaktivní použití. Vlastní ovládací prvek, který <xref:System.Windows.UIElement.OnCreateAutomationPeer%2A> podporuje automatizaci, musí přepsat a <xref:System.Windows.Automation.Peers.AutomationPeer>vrátit instanci třídy, která je odvozena z aplikace . Například pokud vlastní ovládací prvek <xref:System.Windows.Controls.Primitives.ButtonBase> pochází z třídy, <xref:System.Windows.UIElement.OnCreateAutomationPeer%2A> pak <xref:System.Windows.Automation.Peers.ButtonBaseAutomationPeer>objekt vrácený by měl být odvozen z .  
  
 Při implementaci vlastního ovládacího prvku je nutné přepsat metody "Core" ze třídy partnerské třídy základní automatizace, které popisují chování jedinečné a specifické pro vlastní ovládací prvek.  
  
### <a name="override-oncreateautomationpeer"></a>Přepsat onCreateAutomationPeer  
 Přepište <xref:System.Windows.UIElement.OnCreateAutomationPeer%2A> metodu vlastního ovládacího prvku tak, aby vrátil objekt zprostředkovatele, který musí být odvozen přímo nebo nepřímo z aplikace <xref:System.Windows.Automation.Peers.AutomationPeer>.  
  
### <a name="override-getpattern"></a>Přepsat getpattern  
 Partneři automatizace zjednodušují některé [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] aspekty implementace zprostředkovatelů na straně serveru, ale partneři automatizace vlastních ovládacích automatů musí stále zpracovávat rozhraní vzoru. Stejně jako zprostředkovatelé bez WPF podporují partneři vzory řízení <xref:System.Windows.Automation.Provider?displayProperty=nameWithType> tím, že <xref:System.Windows.Automation.Provider.IInvokeProvider>poskytují implementace rozhraní v oboru názvů, například . Rozhraní vzor ovládacího prvku mohou být implementovány peer sám nebo jiným objektem. Implementace partnera <xref:System.Windows.Automation.Peers.AutomationPeer.GetPattern%2A> vrátí objekt, který podporuje zadaný vzor. [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)]kód volá <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetPattern%2A> metodu a <xref:System.Windows.Automation.Peers.PatternInterface> určuje hodnotu výčtu. Přepsání <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetPattern%2A> by měl vrátit objekt, který implementuje zadaný vzor. Pokud váš ovládací prvek nemá vlastní implementaci vzoru, můžete volat základní <xref:System.Windows.Automation.Peers.AutomationPeer.GetPattern%2A> typ implementace načíst buď jeho implementace nebo null, pokud vzor není podporován pro tento typ ovládacího prvku. Například vlastní NumericUpDown ovládací prvek lze nastavit na hodnotu [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] v rozsahu, takže jeho partner by implementovat <xref:System.Windows.Automation.Provider.IRangeValueProvider> rozhraní. Následující příklad ukazuje, jak <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetPattern%2A> je metoda partnera přepsána reagovat na hodnotu. <xref:System.Windows.Automation.Peers.PatternInterface.RangeValue?displayProperty=nameWithType>  
  
 [!code-csharp[CustomControlNumericUpDown#GetPattern](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp/CustomControlLibrary/NumericUpDown.cs#getpattern)]
 [!code-vb[CustomControlNumericUpDown#GetPattern](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic/customcontrollibrary/numericupdown.vb#getpattern)]  
  
 Metoda <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetPattern%2A> můžete také určit dílčí prvek jako zprostředkovatele vzoru. Následující kód ukazuje, jak <xref:System.Windows.Controls.ItemsControl> přenáší zpracování vzorového <xref:System.Windows.Controls.ScrollViewer> procesu posouvání do druhé strany jeho vnitřní kontroly.  
  
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
  
 Chcete-li zadat dílčí prvek pro zpracování vzoru, tento kód získá <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.CreatePeerForElement%2A> objekt subelementu, vytvoří partnera pomocí metody, nastaví <xref:System.Windows.Automation.Peers.AutomationPeer.EventsSource%2A> vlastnost nového partnera na aktuální hod a vrátí nový partner. Nastavení <xref:System.Windows.Automation.Peers.AutomationPeer.EventsSource%2A> na dílčí prvek zabrání dílčí prvek z objevit ve stromu partnerské sítě automatizace a označuje všechny <xref:System.Windows.Automation.Peers.AutomationPeer.EventsSource%2A>události vyvolané dílčí prvek jako pocházející z ovládacího prvku určeného v . Ovládací <xref:System.Windows.Controls.ScrollViewer> prvek se nezobrazí ve stromu automatizace a posouvání události, <xref:System.Windows.Controls.ItemsControl> které generuje zřejmě pocházejí z objektu.  
  
### <a name="override-core-methods"></a>Přepsat "základní" metody  
 Automatizační kód získá informace o vaší ovládací prvku voláním veřejné metody peer třídy. Chcete-li poskytnout informace o ovládacím prvku, přepsat každou metodu, jejíž název končí "Core", když implementace ovládacího prvku se liší od toho, které poskytuje základní automatizace peer třídy. Minimálně ovládací prvek musí <xref:System.Windows.Automation.Peers.AutomationPeer.GetClassNameCore%2A> implementovat a <xref:System.Windows.Automation.Peers.AutomationPeer.GetAutomationControlTypeCore%2A> metody, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[CustomControlNumericUpDown#CoreOverrides](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp/CustomControlLibrary/NumericUpDown.cs#coreoverrides)]
 [!code-vb[CustomControlNumericUpDown#CoreOverrides](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic/customcontrollibrary/numericupdown.vb#coreoverrides)]  
  
 Implementace <xref:System.Windows.Automation.Peers.AutomationPeer.GetAutomationControlTypeCore%2A> popisuje ovládací prvek vrácením <xref:System.Windows.Automation.ControlType> hodnoty. I když <xref:System.Windows.Automation.ControlType.Custom?displayProperty=nameWithType>můžete vrátit , měli byste vrátit jeden z konkrétnější chod ovládacího prvku, pokud přesně popisuje ovládací prvek. Vrácená hodnota <xref:System.Windows.Automation.ControlType.Custom?displayProperty=nameWithType> vyžaduje další práci pro [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)]zprostředkovatele k implementaci a [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] klientské produkty nejsou schopny předvídat strukturu ovládacího prvku, interakci klávesnice a možné vzory ovládacích objektů.  
  
 Implementujte <xref:System.Windows.Automation.Peers.AutomationPeer.IsContentElementCore%2A> <xref:System.Windows.Automation.Peers.AutomationPeer.IsControlElementCore%2A> metody a označující, zda ovládací prvek obsahuje datový obsah nebo plní interaktivní roli v uživatelském rozhraní (nebo obojí). Ve výchozím nastavení `true`vrátí obě metody . Tato nastavení zlepšují použitelnost automatizačních nástrojů, jako jsou programy pro čtení z obrazovky, které mohou tyto metody používat k filtrování stromu automatizace. Pokud <xref:System.Windows.Automation.Peers.AutomationPeer.GetPattern%2A> vaše metoda přenáší zpracování vzorů na partnerské straně <xref:System.Windows.Automation.Peers.AutomationPeer.IsControlElementCore%2A> dílčího prvku, metoda partnerského prvku subelementu může vrátit false skrýt partnerský prvek z automation stromu. Například posouvání v <xref:System.Windows.Controls.ListBox> a je <xref:System.Windows.Controls.ScrollViewer>zpracována a <xref:System.Windows.Automation.Peers.PatternInterface.Scroll?displayProperty=nameWithType> a partner <xref:System.Windows.Automation.Peers.AutomationPeer.GetPattern%2A> pro automatizaci pro je vrácena <xref:System.Windows.Automation.Peers.ScrollViewerAutomationPeer> metodou, která je přidružena k <xref:System.Windows.Automation.Peers.ListBoxAutomationPeer>. Proto <xref:System.Windows.Automation.Peers.AutomationPeer.IsControlElementCore%2A> metoda <xref:System.Windows.Automation.Peers.ScrollViewerAutomationPeer> vrátí `false`tak, aby <xref:System.Windows.Automation.Peers.ScrollViewerAutomationPeer> se nezobrazí ve stromu automatizace.  
  
 Váš partner automatizace by měl poskytnout odpovídající výchozí hodnoty pro váš ovládací prvek. Všimněte si, že XAML, který odkazuje na váš ovládací <xref:System.Windows.Automation.AutomationProperties> prvek můžete přepsat vaše peer implementace základních metod zahrnutím atributy. Například následující XAML vytvoří tlačítko, které [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] má dvě vlastní vlastnosti.  
  
```xaml  
<Button AutomationProperties.Name="Special"
    AutomationProperties.HelpText="This is a special button."/>  
```  
  
### <a name="implement-pattern-providers"></a>Implementovat zprostředkovatele vzorů  
 Rozhraní implementované vlastní zprostředkovatele jsou explicitně deklarovány, <xref:System.Windows.Controls.Control>pokud vlastnící prvek je odvozen přímo z . Například následující kód deklaruje <xref:System.Windows.Controls.Control> partnera pro, který implementuje hodnotu rozsahu.  
  
```csharp  
public class RangePeer1 : FrameworkElementAutomationPeer, IRangeValueProvider { }  
```  
  
```vb  
Public Class RangePeer1  
    Inherits FrameworkElementAutomationPeer  
    Implements IRangeValueProvider  
End Class  
```  
  
 Pokud vlastnící ovládací prvek pochází z určitého <xref:System.Windows.Controls.Primitives.RangeBase>typu ovládacího prvku, jako je například , může být druhá strana odvozena z ekvivalentní odvozené třídy rovnocenných partnerů. V tomto případě by peer <xref:System.Windows.Automation.Peers.RangeBaseAutomationPeer>odvodit z <xref:System.Windows.Automation.Provider.IRangeValueProvider>, který poskytuje základní implementaci . Následující kód ukazuje prohlášení takového partnera.  
  
```csharp  
public class RangePeer2 : RangeBaseAutomationPeer { }  
```  
  
```vb  
Public Class RangePeer2  
    Inherits RangeBaseAutomationPeer  
End Class  
```  
  
Příklad implementace naleznete [c#](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp) nebo [visual basic](https://github.com/dotnet/docs/tree/master/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic) zdrojový kód, který implementuje a spotřebovává NumericUpDown vlastní ovládací prvek.  
  
### <a name="raise-events"></a>Zvýšit události  
 Klienti automatizace se mohou přihlásit k odběru událostí automatizace. Vlastní ovládací prvky musí hlásit <xref:System.Windows.Automation.Peers.AutomationPeer.RaiseAutomationEvent%2A> změny stavu ovládacího prvku voláním metody. Podobně při změně hodnoty vlastnosti <xref:System.Windows.Automation.Peers.AutomationPeer.RaisePropertyChangedEvent%2A> volání metody. Následující kód ukazuje, jak získat peer objekt z v rámci řídicího kódu a volání metody pro zvýšení události. Jako optimalizace kód určuje, zda existují všechny posluchače pro tento typ události. Vyvolání události pouze v případě, že jsou posluchači vyhnout zbytečné režie a pomáhá ovládací prvek zůstat responzivní.  
  
 [!code-csharp[CustomControlNumericUpDown#RaiseEventFromControl](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp/CustomControlLibrary/NumericUpDown.cs#raiseeventfromcontrol)]
 [!code-vb[CustomControlNumericUpDown#RaiseEventFromControl](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic/customcontrollibrary/numericupdown.vb#raiseeventfromcontrol)]  
  
## <a name="see-also"></a>Viz také

- [Přehled automatizace uživatelského rozhraní](../../ui-automation/ui-automation-overview.md)
- [Implementace zprostředkovatele automatizace uživatelského rozhraní na straně serveru](../../ui-automation/server-side-ui-automation-provider-implementation.md)
- [Vlastní ovládací prvek NumericUpDown (C#) na GitHubu](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp)  
- [Vlastní ovládací prvek NumericUpDown (Visual Basic) na GitHubu](https://github.com/dotnet/docs/tree/master/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic)
