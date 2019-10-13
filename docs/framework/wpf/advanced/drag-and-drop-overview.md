---
title: Přehled přetažení
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- drag-and-drop [WPF], implementing
- drag sources [WPF], drag-and-drop
- data transfer [WPF], drag-and-drop
- drag-and-drop [WPF], about
- drag-and-drop [WPF], events
- drop targets [WPF], drag-and-drop
ms.assetid: 1a5b27b0-0ac5-4cdf-86c0-86ac0271fa64
ms.openlocfilehash: 72dc443e5653b9871c3f67b003bd1af0536d5993
ms.sourcegitcommit: 9c3a4f2d3babca8919a1e490a159c1500ba7a844
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2019
ms.locfileid: "72291471"
---
# <a name="drag-and-drop-overview"></a>Přehled přetažení
V tomto tématu najdete přehled podpory přetahování myší v aplikacích [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. Přetahování obvykle odkazuje na metodu přenosu dat, která zahrnuje použití myši (nebo jiného polohovacího zařízení) k výběru jednoho nebo více objektů, přetažením těchto objektů přes některý požadovaný cíl přetažení v [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] a jejich vyřazení.  

<a name="Drag_and_Drop_Support"></a>   
## <a name="drag-and-drop-support-in-wpf"></a>Podpora přetažení v subsystému WPF  
 Operace přetažení obvykle zahrnují dvě strany: zdroj přetažení, ze kterého přetažený objekt pochází, a cíl přetažení, který přijímá vyřazený objekt.  Cíl přetažení zdroje a přetažením může být prvky uživatelského rozhraní ve stejné aplikaci nebo v jiné aplikaci.  
  
 Typ a počet objektů, u kterých lze manipulovat přetažením, je zcela libovolný. Například soubory, složky a výběry obsahu jsou některé z nejběžnějších objektů, které jsou zpracovávány pomocí operací přetažení.  
  
 Konkrétní akce provedené během operace přetažení jsou specifické pro aplikace a často určené podle kontextu.  Například přetažení výběru souborů z jedné složky do druhé na stejné paměťové zařízení přesune soubory ve výchozím nastavení, zatímco při přetahování souborů ze sdílené složky UNC (Universal Naming Convention) do místní složky se soubory ve výchozím nastavení zkopírují.  
  
 Zařízení přetahování, která poskytuje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], jsou navržená tak, aby byla vysoce flexibilní a přizpůsobitelná, aby podporovala širokou škálu scénářů přetažení.  Přetahování myší podporuje manipulaci s objekty v rámci jedné aplikace nebo mezi různými aplikacemi. Přetahování mezi aplikacemi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a dalšími aplikacemi systému Windows je také plně podporováno.  
  
 V [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] se může <xref:System.Windows.UIElement> nebo <xref:System.Windows.ContentElement> účastnit přetahování myší. Události a metody požadované pro operace přetažení jsou definovány ve třídě <xref:System.Windows.DragDrop>. Třídy <xref:System.Windows.UIElement> a <xref:System.Windows.ContentElement> obsahují aliasy pro události připojené <xref:System.Windows.DragDrop> tak, aby se události zobrazovaly v seznamu členů třídy, když je <xref:System.Windows.UIElement> nebo <xref:System.Windows.ContentElement> zděděn jako základní prvek. Obslužné rutiny událostí, které jsou připojeny k těmto událostem, jsou připojeny k základní události <xref:System.Windows.DragDrop> připojené a získají stejnou instanci dat události. Další informace najdete v tématu událost @no__t 0.  
  
> [!IMPORTANT]
> Přetahování OLE v zóně Internet nefunguje.  
  
<a name="Data_Transfer"></a>   
## <a name="data-transfer"></a>Přenos dat  
 Přetahování je součástí obecnější oblasti přenosu dat. Přenos dat zahrnuje operace přetažení a kopírování a vložení. Operace přetažení se podobá operaci kopírování a vložení nebo vyjmutí a vložení, která se používá k přenosu dat z jednoho objektu nebo aplikace do jiné pomocí systémové schránky. Oba typy operací vyžadují:  
  
- Zdrojový objekt, který poskytuje data.  
  
- Způsob dočasného uložení přenesených dat.  
  
- Cílový objekt, který přijímá data.  
  
 V rámci operace kopírování a vkládání se systémová schránka používá k dočasnému uložení přenesených dat; Při operaci přetažení se k ukládání dat používá <xref:System.Windows.DataObject>. V koncepčním datovém objektu se skládá z jedné nebo více párů <xref:System.Object>, který obsahuje skutečná data a odpovídající identifikátor formátu dat.  
  
 Zdroj přetažení inicializuje operaci přetažení voláním statické metody <xref:System.Windows.DragDrop.DoDragDrop%2A?displayProperty=nameWithType> a předáním přenesených dat. Metoda <xref:System.Windows.DragDrop.DoDragDrop%2A> automaticky zalomí data v <xref:System.Windows.DataObject> v případě potřeby. Pro lepší kontrolu nad formátem dat můžete data vložit do <xref:System.Windows.DataObject> předtím, než je předáte do metody <xref:System.Windows.DragDrop.DoDragDrop%2A>. Cíl přetažení zodpovídá za extrakci dat z <xref:System.Windows.DataObject>. Další informace o práci s datovými objekty naleznete v tématu [data a datové objekty](data-and-data-objects.md).  
  
 Zdroj a cíl operace přetažení jsou prvky uživatelského rozhraní. data, která se skutečně přenáší, ale většinou nemají vizuální znázornění. Můžete napsat kód, který poskytuje vizuální reprezentaci dat, která jsou přetažena, například nastane při přetahování souborů v Průzkumníkovi Windows. Ve výchozím nastavení se uživateli poskytuje zpětná vazba tím, že změní kurzor tak, aby představoval vliv operace přetažení na data, například zda budou data přesunuta nebo zkopírována.  
  
### <a name="drag-and-drop-effects"></a>Efekty přetažení  
 Operace přetažení mohou mít různé účinky na přenášená data. Data můžete například zkopírovat nebo je můžete přesunout. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] definuje výčet <xref:System.Windows.DragDropEffects>, který můžete použít k určení účinku operace přetažení. Ve zdroji přetažením můžete určit efekty, které bude zdroj umožňovat v metodě <xref:System.Windows.DragDrop.DoDragDrop%2A>. V cíli přetažení můžete zadat efekt, který cíl zamýšlí v vlastnosti <xref:System.Windows.DragEventArgs.Effects%2A> třídy <xref:System.Windows.DragEventArgs>. Pokud cíl přetažení určuje zamýšlený efekt v události <xref:System.Windows.DragDrop.DragOver>, tyto informace se předávají zpět do zdroje přetažení v události <xref:System.Windows.DragDrop.GiveFeedback>. Zdroj přetažení používá tyto informace k informování uživatele o tom, jaký vliv má cíl přetažení na data. Když jsou data vyřazena, cíl přetažení určuje jeho skutečný efekt v události <xref:System.Windows.DragDrop.Drop>. Tyto informace jsou předány zpět do zdroje přetažení jako návratová hodnota metody <xref:System.Windows.DragDrop.DoDragDrop%2A>. Pokud cíl přetažení vrátí efekt, který není v seznamu přetažení zdrojů `allowedEffects`, operace přetažení se zruší, aniž by došlo k jakémukoli přenosu dat.  
  
 Je důležité si uvědomit, že v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] se hodnoty <xref:System.Windows.DragDropEffects> používají pouze k zajištění komunikace mezi zdrojem přetažení a cílem přetažení, a to z hlediska vlivu operace přetažení. Skutečný účinek operace přetažení závisí na tom, jak v aplikaci napsat příslušný kód.  
  
 Cíl přetažení může například specifikovat, že vlivem přesunu dat na je přesouvání dat. Chcete-li však přesunout data, musí být přidána do cílového prvku a odebrán ze zdrojového elementu. Zdrojový element může indikovat, že umožňuje přesun dat, ale pokud neposkytnete kód pro odebrání dat ze zdrojového elementu, konečný výsledek bude zkopírován a nebude přesunut.  
  
<a name="Drag_and_Drop_Events"></a>   
## <a name="drag-and-drop-events"></a>Události přetažení  
 Operace přetažení podporují model řízený událostmi.  Zdrojový zdroj i cíl přetažení používají ke zpracování operací přetažení standardní sadu událostí.  Následující tabulky shrnují standardní události přetažení myší. Jedná se o připojené události ke třídě <xref:System.Windows.DragDrop>. Další informace o připojených událostech najdete v tématu [Přehled připojených událostí](attached-events-overview.md).  
  
### <a name="drag-source-events"></a>Přetáhněte zdrojové události  
  
|Událost|Souhrn|  
|-----------|-------------|  
|<xref:System.Windows.DragDrop.GiveFeedback>|Tato událost probíhá nepřetržitě během operace přetažení a umožňuje zdroji přetažení poskytnout uživateli informace o zpětné vazbě. Tato zpětná vazba je obvykle dána změnou vzhledu ukazatele myši k označení efektů povolených cílem přetažení.  Toto je probublávání událost.|  
|<xref:System.Windows.DragDrop.QueryContinueDrag>|Tato událost nastane, když dojde ke změně v stavech tlačítek klávesnice nebo myši během operace přetažení a umožňuje, aby se zdroj přetažení zrušil v závislosti na stavu klíče nebo tlačítka. Toto je probublávání událost.|  
|<xref:System.Windows.DragDrop.PreviewGiveFeedback>|TUNELING verze <xref:System.Windows.DragDrop.GiveFeedback>.|  
|<xref:System.Windows.DragDrop.PreviewQueryContinueDrag>|TUNELING verze <xref:System.Windows.DragDrop.QueryContinueDrag>.|  
  
### <a name="drop-target-events"></a>Vyřadit cílové události  
  
|Událost|Souhrn|  
|-----------|-------------|  
|<xref:System.Windows.DragDrop.DragEnter>|Tato událost nastane, pokud je objekt přetažen do hranice cíle přetažení. Toto je probublávání událost.|  
|<xref:System.Windows.DragDrop.DragLeave>|Tato událost nastane, pokud je objekt přetažen mimo hranici cíle přetažení.  Toto je probublávání událost.|  
|<xref:System.Windows.DragDrop.DragOver>|Tato událost probíhá průběžně při přetahování objektu (přesunuto) v rámci hranice cílového umístění. Toto je probublávání událost.|  
|<xref:System.Windows.DragDrop.Drop>|Tato událost nastane, pokud je objekt v cíli přetažení vyřazen.  Toto je probublávání událost.|  
|<xref:System.Windows.DragDrop.PreviewDragEnter>|TUNELING verze <xref:System.Windows.DragDrop.DragEnter>.|  
|<xref:System.Windows.DragDrop.PreviewDragLeave>|TUNELING verze <xref:System.Windows.DragDrop.DragLeave>.|  
|<xref:System.Windows.DragDrop.PreviewDragOver>|TUNELING verze <xref:System.Windows.DragDrop.DragOver>.|  
|<xref:System.Windows.DragDrop.PreviewDrop>|TUNELING verze <xref:System.Windows.DragDrop.Drop>.|  
  
 Chcete-li zpracovat události přetažení pro instance objektu, přidejte obslužné rutiny pro události uvedené v předchozích tabulkách. Chcete-li zpracovat události přetažení na úrovni třídy, přepište odpovídající virtuální událost on * a metody @ no__t-0PreviewEvent. Další informace naleznete v tématu [zpracování tříd směrovaných událostí pomocí ovládacích prvků základní třídy](marking-routed-events-as-handled-and-class-handling.md#Class_Handling_of_Routed_Events).  
  
<a name="Implementing_Drag_And_Drop"></a>   
## <a name="implementing-drag-and-drop"></a>Implementace přetažení myší  
 Prvek uživatelského rozhraní může být zdroj přetažení, cíl přetažení nebo obojí. Chcete-li implementovat základní přetahování, napíšete kód pro zahájení operace přetažení a zpracování vyřazených dat. Můžete rozšířit možnosti přetahování pomocí zpracování volitelných událostí přetažení.  
  
 K implementaci základních přetahování budete provádět následující úlohy:  
  
- Identifikujte prvek, který bude zdrojem přetažení. Zdroj přetažení může být <xref:System.Windows.UIElement> nebo <xref:System.Windows.ContentElement>.  
  
- Vytvořte obslužnou rutinu události ve zdroji přetažení, který spustí operaci přetažení. Událost je typicky událost <xref:System.Windows.UIElement.MouseMove>.  
  
- V obslužné rutině zdrojové události přetažení zavolejte metodu <xref:System.Windows.DragDrop.DoDragDrop%2A> pro zahájení operace přetažení. V volání <xref:System.Windows.DragDrop.DoDragDrop%2A> určete zdroj přetažení, data, která mají být přenesena, a povolené efekty.  
  
- Identifikujte prvek, který bude cílem přetažení. Cíl přetažení může být <xref:System.Windows.UIElement> nebo <xref:System.Windows.ContentElement>.  
  
- V poli cíl přetažení nastavte vlastnost <xref:System.Windows.UIElement.AllowDrop%2A> na hodnotu `true`.  
  
- V cíli přetažení vytvořte obslužnou rutinu události <xref:System.Windows.DragDrop.Drop> pro zpracování zahozených dat.  
  
- V obslužné rutině události <xref:System.Windows.DragDrop.Drop> rozbalte data z <xref:System.Windows.DragEventArgs> pomocí metod <xref:System.Windows.DataObject.GetDataPresent%2A> a <xref:System.Windows.DataObject.GetData%2A>.  
  
- V obslužné rutině události <xref:System.Windows.DragDrop.Drop> použijte k provedení požadované operace přetažení data.  
  
 Implementaci přetahování můžete vylepšit tím, že vytvoříte vlastní <xref:System.Windows.DataObject> a vyřadíte volitelné události přetažení zdroje a přetažením, jak je znázorněno v následujících úlohách:  
  
- Chcete-li přenést vlastní data nebo více datových položek, vytvořte <xref:System.Windows.DataObject> pro předání metodě <xref:System.Windows.DragDrop.DoDragDrop%2A>.  
  
- Chcete-li provést další akce během přetahování, zpracujte v cíli přetažení události <xref:System.Windows.DragDrop.DragEnter>, <xref:System.Windows.DragDrop.DragOver> a <xref:System.Windows.DragDrop.DragLeave>.  
  
- Chcete-li změnit vzhled ukazatele myši, zpracujte u zdroje přetažení událost <xref:System.Windows.DragDrop.GiveFeedback>.  
  
- Chcete-li změnit způsob zrušení operace přetažení, zpracujte u zdroje přetažení událost <xref:System.Windows.DragDrop.QueryContinueDrag>.  
  
<a name="Drag_And_Drop_Example"></a>   
## <a name="drag-and-drop-example"></a>Příklad přetahování myší  
 Tato část popisuje, jak implementovat přetažení pro @no__t element-0. @No__t-0 je jak zdroj přetažení, tak i cíl přetažení. Přenesená data jsou řetězcová reprezentace vlastnosti @no__t 0 elipsy. Následující kód XAML ukazuje prvek <xref:System.Windows.Shapes.Ellipse> a události související s přetahováním, které zpracovává. Úplný postup, jak implementovat přetahování, najdete v tématu [Návod: povolení přetahování na uživatelském ovládacím prvku](walkthrough-enabling-drag-and-drop-on-a-user-control.md).  
  
 [!code-xaml[DragDropSnippets#EllipseXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml#ellipsexaml)]  
  
### <a name="enabling-an-element-to-be-a-drag-source"></a>Povolení prvku jako zdroje přetažení  
 Objekt, který je zdrojem přetažení, zodpovídá za:  
  
- Určení, kdy dojde k přetahování.  
  
- Zahajuje se operace přetažení.  
  
- Identifikují se data, která se mají přenést.  
  
- Určení vlivu operace přetažení na přenášená data.  
  
 Zdroj přetažení může také uživateli poskytnout zpětnou vazbu týkající se povolených akcí (přesunutí, kopírování, žádné) a může zrušit operaci přetažení na základě dalšího vstupu uživatele, například při stisknutí klávesy ESC během tažení.  
  
 Je zodpovědností vaší aplikace na určení, kdy dojde k přetahování, a následnou inicializací operace přetažení voláním metody <xref:System.Windows.DragDrop.DoDragDrop%2A>. Obvykle se jedná o situaci, kdy při stisknutí tlačítka myši dojde k události <xref:System.Windows.UIElement.MouseMove> nad prvkem, který se má přetáhnout. Následující příklad ukazuje, jak iniciovat operaci přetažení z obslužné rutiny události <xref:System.Windows.UIElement.MouseMove> elementu <xref:System.Windows.Shapes.Ellipse>, aby byla přetažena na zdroj. Přenesená data jsou řetězcová reprezentace vlastnosti @no__t 0 elipsy.  
  
 [!code-csharp[DragDropSnippets#DoDragDrop](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#dodragdrop)]
 [!code-vb[DragDropSnippets#DoDragDrop](~/samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#dodragdrop)]  
  
 Uvnitř obslužné rutiny události <xref:System.Windows.UIElement.MouseMove> zavolejte metodu <xref:System.Windows.DragDrop.DoDragDrop%2A> pro zahájení operace přetažení. Metoda <xref:System.Windows.DragDrop.DoDragDrop%2A> přijímá tři parametry:  
  
- `dragSource` – odkaz na objekt závislosti, který je zdrojem přenesených dat; obvykle se jedná o zdroj události <xref:System.Windows.UIElement.MouseMove>.  
  
- `data` – objekt obsahující přenesená data zabalená do <xref:System.Windows.DataObject>.  
  
- `allowedEffects`-jedna z hodnot výčtu <xref:System.Windows.DragDropEffects>, která určuje povolené účinky operace přetažení.  
  
 Libovolný serializovatelný objekt lze předat v parametru `data`. Pokud data ještě nejsou zabalená do <xref:System.Windows.DataObject>, automaticky se zabalí do nového <xref:System.Windows.DataObject>. Chcete-li předat více datových položek, je nutné vytvořit <xref:System.Windows.DataObject> sami a předat ji metodě <xref:System.Windows.DragDrop.DoDragDrop%2A>. Další informace najdete v tématu [data a datové objekty](data-and-data-objects.md).  
  
 Parametr `allowedEffects` slouží k určení toho, jak bude zdroj přetažení umožňovat přenesené data. Společné hodnoty pro zdroj přetažení jsou <xref:System.Windows.DragDropEffects.Copy>, <xref:System.Windows.DragDropEffects.Move> a <xref:System.Windows.DragDropEffects.All>.  
  
> [!NOTE]
> Cíl přetažení také umožňuje určit, jaké účinky má v reakci na Vyřazená data. Například pokud cíl přetažení nerozpozná datový typ, který má být vyřazen, může data odmítnout nastavením jeho povolených efektů na <xref:System.Windows.DragDropEffects.None>. Obvykle to dělá v obslužné rutině události <xref:System.Windows.DragDrop.DragOver>.  
  
 Zdroj přetažení může volitelně zpracovávat události <xref:System.Windows.DragDrop.GiveFeedback> a <xref:System.Windows.DragDrop.QueryContinueDrag>. Tyto události mají výchozí obslužné rutiny, které se používají, pokud události neoznačíte jako zpracovávané. Tyto události obvykle budete ignorovat, pokud nemáte konkrétní nutnost změnit jejich výchozí chování.  
  
 Událost <xref:System.Windows.DragDrop.GiveFeedback> se vyvolává průběžně při přetahování zdroje. Výchozí obslužná rutina této události kontroluje, zda je zdroj přetažení přes platný cíl přetažení. Pokud je, kontroluje povolené účinky cíle přetažení. Pak poskytne zpětné vazby koncovému uživateli týkající se povolených efektů odkládacího pole. To se obvykle provádí změnou ukazatele myši na kurzor bez přetažení, kopírování nebo přesunutí. Tuto událost byste měli zpracovat pouze v případě, že potřebujete použít vlastní kurzory k poskytnutí zpětné vazby uživateli. Pokud tuto událost pořídíte, nezapomeňte ji označit jako zpracovanou, aby výchozí obslužná rutina nepsala vaši obslužnou rutinu.  
  
 Událost <xref:System.Windows.DragDrop.QueryContinueDrag> se vyvolává průběžně při přetahování zdroje. Tuto událost můžete zpracovat a určit tak, která akce ukončí operaci přetažení na základě stavu kláves ESC, SHIFT, CTRL a ALT a také stavu tlačítek myši. Výchozí obslužná rutina pro tuto událost zruší operaci přetažení, pokud je stisknuta klávesa ESC, a když dojde k uvolnění tlačítka myši, data se zruší.  
  
> [!CAUTION]
> Tyto události jsou během operace přetažení vyvolány průběžně. Proto byste se měli vyhnout úlohám náročným na prostředky v obslužných rutinách událostí.  Při každém vyvolání události <xref:System.Windows.DragDrop.GiveFeedback> můžete například použít ukazatel v mezipaměti místo vytvoření nového kurzoru.  
  
### <a name="enabling-an-element-to-be-a-drop-target"></a>Povolení prvku jako cíle přetažení  
 Objekt, který je cílem přetažení, zodpovídá za:  
  
- Určení, že se jedná o platný cíl přetažení.  
  
- Reaguje na zdroj přetažení při přetahování přes cíl.  
  
- Kontrola, zda jsou přenesená data ve formátu, který může přijímat.  
  
- Zpracování vynechaných dat.  
  
 Chcete-li určit, že prvek je cílem přetažení, nastavte jeho vlastnost <xref:System.Windows.UIElement.AllowDrop%2A> na hodnotu `true`. Události cíle přetažení budou následně vyvolány na prvek, aby bylo možné je zpracovat. Během operace přetažení dojde v cíli přetažení k následující posloupnosti událostí:  
  
1. <xref:System.Windows.DragDrop.DragEnter>  
  
2. <xref:System.Windows.DragDrop.DragOver>  
  
3. <xref:System.Windows.DragDrop.DragLeave> nebo <xref:System.Windows.DragDrop.Drop>  
  
 Událost <xref:System.Windows.DragDrop.DragEnter> nastane, pokud jsou data přetažena do hranice cíle přetažení. Tato událost se obvykle zpracovává, aby poskytovala náhled efektů operace přetažení, pokud je to vhodné pro vaši aplikaci. Nenastavte vlastnost <xref:System.Windows.DragEventArgs.Effects%2A?displayProperty=nameWithType> v události <xref:System.Windows.DragDrop.DragEnter>, protože bude přepsána v události <xref:System.Windows.DragDrop.DragOver>.  
  
 Následující příklad ukazuje obslužnou rutinu události <xref:System.Windows.DragDrop.DragEnter> pro prvek <xref:System.Windows.Shapes.Ellipse>. Tento kód zobrazí náhled efektů operace přetažení uložením aktuálního štětce <xref:System.Windows.Shapes.Shape.Fill%2A>. Potom používá metodu <xref:System.Windows.DataObject.GetDataPresent%2A> ke kontrole, zda <xref:System.Windows.DataObject> přetaženo přes elipsu obsahuje řetězcová data, která lze převést na <xref:System.Windows.Media.Brush>. V takovém případě se data extrahují pomocí metody <xref:System.Windows.DataObject.GetData%2A>. Pak se převede na <xref:System.Windows.Media.Brush> a použije se na elipsu. Změna se vrátí v obslužné rutině události <xref:System.Windows.DragDrop.DragLeave>. Pokud data nelze převést na <xref:System.Windows.Media.Brush>, není provedena žádná akce.  
  
 [!code-csharp[DragDropSnippets#DragEnter](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#dragenter)]
 [!code-vb[DragDropSnippets#DragEnter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#dragenter)]  
  
 Událost <xref:System.Windows.DragDrop.DragOver> probíhá nepřetržitě, zatímco data jsou přetažena přes cíl přetažení. Tato událost se spáruje s událostí <xref:System.Windows.DragDrop.GiveFeedback> na zdroji přetažení. V obslužné rutině události <xref:System.Windows.DragDrop.DragOver> obvykle používáte metody <xref:System.Windows.DataObject.GetDataPresent%2A> a <xref:System.Windows.DataObject.GetData%2A> ke kontrole, zda jsou přenesená data ve formátu, který může cíl přetažení zpracovat. Můžete také ověřit, zda jsou stisknuty jakékoli modifikační klávesy, což obvykle indikuje, zda uživatel zamýšlí akci přesunutí nebo kopírování. Po provedení těchto kontrol nastavíte vlastnost <xref:System.Windows.DragEventArgs.Effects%2A?displayProperty=nameWithType> tak, aby upozornila zdroj přetažení, který bude mít za následek odstranění dat. Zdroj přetažení obdrží tyto informace v argumentech události <xref:System.Windows.DragDrop.GiveFeedback> a může nastavit vhodný ukazatel na poskytnutí zpětné vazby uživateli.  
  
 Následující příklad ukazuje obslužnou rutinu události <xref:System.Windows.DragDrop.DragOver> pro prvek <xref:System.Windows.Shapes.Ellipse>. Tento kód zkontroluje, zda <xref:System.Windows.DataObject> přetaženo přes elipsu obsahuje řetězcová data, která lze převést na <xref:System.Windows.Media.Brush>. Pokud ano, nastaví vlastnost <xref:System.Windows.DragEventArgs.Effects%2A?displayProperty=nameWithType> na hodnotu <xref:System.Windows.DragDropEffects.Copy>. To znamená, že zdroj přetažení je možné zkopírovat data do elipsy. Pokud data nelze převést na <xref:System.Windows.Media.Brush>, vlastnost <xref:System.Windows.DragEventArgs.Effects%2A?displayProperty=nameWithType> je nastavena na hodnotu <xref:System.Windows.DragDropEffects.None>. To označuje zdroj přetažení, že elipsa není platným cílem přetažení pro data.  
  
 [!code-csharp[DragDropSnippets#DragOver](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#dragover)]
 [!code-vb[DragDropSnippets#DragOver](~/samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#dragover)]  
  
 Událost <xref:System.Windows.DragDrop.DragLeave> nastane, pokud jsou data přetažena mimo hranici cíle bez vyřazení. Tato událost se zpracovává za účelem vrácení všeho, co jste provedli v obslužné rutině události <xref:System.Windows.DragDrop.DragEnter>.  
  
 Následující příklad ukazuje obslužnou rutinu události <xref:System.Windows.DragDrop.DragLeave> pro prvek <xref:System.Windows.Shapes.Ellipse>. Tento kód vrátí náhled provedený v obslužné rutině události <xref:System.Windows.DragDrop.DragEnter> použitím uloženého <xref:System.Windows.Media.Brush> na tři tečky.  
  
 [!code-csharp[DragDropSnippets#DragLeave](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#dragleave)]
 [!code-vb[DragDropSnippets#DragLeave](~/samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#dragleave)]  
  
 Událost <xref:System.Windows.DragDrop.Drop> nastane, pokud jsou data přehozena přes cíl přetažení; ve výchozím nastavení k tomu dojde, když se uvolní tlačítko myši. V obslužné rutině události <xref:System.Windows.DragDrop.Drop> použijete metodu <xref:System.Windows.DataObject.GetData%2A> k extrakci přenesených dat z <xref:System.Windows.DataObject> a provádíte veškerá zpracování dat, která vaše aplikace vyžaduje. Událost <xref:System.Windows.DragDrop.Drop> ukončí operaci přetažení.  
  
 Následující příklad ukazuje obslužnou rutinu události <xref:System.Windows.DragDrop.Drop> pro prvek <xref:System.Windows.Shapes.Ellipse>. Tento kód používá účinky operace přetažení a je podobný kódu v obslužné rutině události <xref:System.Windows.DragDrop.DragEnter>. Kontroluje, zda <xref:System.Windows.DataObject> přetaženo přes elipsu obsahuje řetězcová data, která lze převést na <xref:System.Windows.Media.Brush>. V takovém případě se na elipsu použije <xref:System.Windows.Media.Brush>. Pokud data nelze převést na <xref:System.Windows.Media.Brush>, není provedena žádná akce.  
  
 [!code-csharp[DragDropSnippets#Drop](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#drop)]
 [!code-vb[DragDropSnippets#Drop](~/samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#drop)]  
  
## <a name="see-also"></a>Další informace najdete v tématech

- <xref:System.Windows.Clipboard>
- [Návod: povolení přetahování na uživatelském ovládacím prvku](walkthrough-enabling-drag-and-drop-on-a-user-control.md)
- [Témata s postupy](drag-and-drop-how-to-topics.md)
- [Přetažení](drag-and-drop.md)
