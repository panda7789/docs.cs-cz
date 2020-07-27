---
title: Přehled přetažení
description: Seznamte se s podporou přetahování myší v aplikacích Windows Presentation Foundation, která umožňuje uživatelům přetahovat objekty do oblasti v uživatelském rozhraní.
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
ms.openlocfilehash: 63384e79d8a198e4cc9507ca3266c484c0506e2c
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168067"
---
# <a name="drag-and-drop-overview"></a>Přehled přetažení
V tomto tématu najdete přehled podpory přetahování v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikacích. Přetahování obvykle odkazuje na metodu přenosu dat, která zahrnuje použití myši (nebo jiného polohovacího zařízení) k výběru jednoho nebo více objektů, přetažením těchto objektů přes některý požadovaný cíl přetažení v a jejich přetažení [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] .  

<a name="Drag_and_Drop_Support"></a>
## <a name="drag-and-drop-support-in-wpf"></a>Podpora přetažení v subsystému WPF  
 Operace přetažení obvykle zahrnují dvě strany: zdroj přetažení, ze kterého přetažený objekt pochází, a cíl přetažení, který přijímá vyřazený objekt.  Cíl přetažení zdroje a přetažením může být prvky uživatelského rozhraní ve stejné aplikaci nebo v jiné aplikaci.  
  
 Typ a počet objektů, u kterých lze manipulovat přetažením, je zcela libovolný. Například soubory, složky a výběry obsahu jsou některé z nejběžnějších objektů, které jsou zpracovávány pomocí operací přetažení.  
  
 Konkrétní akce provedené během operace přetažení jsou specifické pro aplikace a často určené podle kontextu.  Například přetažení výběru souborů z jedné složky do druhé na stejné paměťové zařízení přesune soubory ve výchozím nastavení, zatímco při přetahování souborů ze sdílené složky UNC (Universal Naming Convention) do místní složky se soubory ve výchozím nastavení zkopírují.  
  
 Zařízení přetažení, která poskytuje, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jsou navržená tak, aby byla vysoce flexibilní a přizpůsobitelná, aby podporovala širokou škálu scénářů přetažení.  Přetahování myší podporuje manipulaci s objekty v rámci jedné aplikace nebo mezi různými aplikacemi. Přetahování mezi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacemi a dalšími aplikacemi Windows je také plně podporováno.  
  
 V [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] , Any <xref:System.Windows.UIElement> nebo se <xref:System.Windows.ContentElement> může účastnit přetahování myší. Události a metody požadované pro operace přetažení jsou definovány ve <xref:System.Windows.DragDrop> třídě. <xref:System.Windows.UIElement>Třídy a <xref:System.Windows.ContentElement> obsahují aliasy pro <xref:System.Windows.DragDrop> připojené události, aby se události zobrazovaly v seznamu členů třídy, když <xref:System.Windows.UIElement> je nebo <xref:System.Windows.ContentElement> zděděn jako základní prvek. Obslužné rutiny událostí, které jsou připojeny k těmto událostem, jsou připojeny k základní <xref:System.Windows.DragDrop> připojené události a získají stejnou instanci dat události. Další informace najdete v tématu <xref:System.Windows.UIElement.Drop?displayProperty=nameWithType> událost.  
  
> [!IMPORTANT]
> Přetahování OLE v zóně Internet nefunguje.  
  
<a name="Data_Transfer"></a>
## <a name="data-transfer"></a>Přenos dat  
 Přetahování je součástí obecnější oblasti přenosu dat. Přenos dat zahrnuje operace přetažení a kopírování a vložení. Operace přetažení se podobá operaci kopírování a vložení nebo vyjmutí a vložení, která se používá k přenosu dat z jednoho objektu nebo aplikace do jiné pomocí systémové schránky. Oba typy operací vyžadují:  
  
- Zdrojový objekt, který poskytuje data.  
  
- Způsob dočasného uložení přenesených dat.  
  
- Cílový objekt, který přijímá data.  
  
 V rámci operace kopírování a vkládání se systémová schránka používá k dočasnému uložení přenesených dat; Při operaci přetažení <xref:System.Windows.DataObject> se k ukládání dat používá. V koncepčním datovém objektu se skládá z jedné nebo více párů obsahující <xref:System.Object> skutečná data a odpovídající identifikátor formátu dat.  
  
 Zdroj přetažení inicializuje operaci přetažení voláním statické <xref:System.Windows.DragDrop.DoDragDrop%2A?displayProperty=nameWithType> metody a předáním přenesených dat. <xref:System.Windows.DragDrop.DoDragDrop%2A>Metoda automaticky zalomí data v <xref:System.Windows.DataObject> případě potřeby. Pro lepší kontrolu nad formátem dat můžete <xref:System.Windows.DataObject> před předáním do metody zabalit data <xref:System.Windows.DragDrop.DoDragDrop%2A> . Cíl přetažení zodpovídá za extrakci dat z <xref:System.Windows.DataObject> . Další informace o práci s datovými objekty naleznete v tématu [data a datové objekty](data-and-data-objects.md).  
  
 Zdroj a cíl operace přetažení jsou prvky uživatelského rozhraní. data, která se skutečně přenáší, ale většinou nemají vizuální znázornění. Můžete napsat kód, který poskytuje vizuální reprezentaci dat, která jsou přetažena, například nastane při přetahování souborů v Průzkumníkovi Windows. Ve výchozím nastavení se uživateli poskytuje zpětná vazba tím, že změní kurzor tak, aby představoval vliv operace přetažení na data, například zda budou data přesunuta nebo zkopírována.  
  
### <a name="drag-and-drop-effects"></a>Efekty přetažení  
 Operace přetažení mohou mít různé účinky na přenášená data. Data můžete například zkopírovat nebo je můžete přesunout. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]definuje <xref:System.Windows.DragDropEffects> výčet, který můžete použít k určení účinku operace přetažení. Ve zdroji přetažením můžete určit efekty, které bude zdroj v <xref:System.Windows.DragDrop.DoDragDrop%2A> metodě umožňovat. V cíli přetažení můžete zadat efekt, který cíl zamýšlí ve <xref:System.Windows.DragEventArgs.Effects%2A> vlastnosti <xref:System.Windows.DragEventArgs> třídy. Když cíl přetažení určuje zamýšlený efekt v <xref:System.Windows.DragDrop.DragOver> události, tyto informace se předávají zpět do zdroje přetažení v <xref:System.Windows.DragDrop.GiveFeedback> události. Zdroj přetažení používá tyto informace k informování uživatele o tom, jaký vliv má cíl přetažení na data. Když jsou data vyřazena, cíl přetažení určuje jeho skutečný účinek v <xref:System.Windows.DragDrop.Drop> události. Tyto informace jsou předány zpět do zdroje přetažení jako návratová hodnota <xref:System.Windows.DragDrop.DoDragDrop%2A> metody. Pokud cíl přetažení vrátí efekt, který není v seznamu zdrojů pro přetažení `allowedEffects` , operace přetažení se zruší, aniž by došlo k přenosu dat.  
  
 Je důležité si uvědomit, že v systému se [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.DragDropEffects> hodnoty používají pouze k zajištění komunikace mezi zdrojem přetažení a cílem přetažení z hlediska efektů operace přetažení. Skutečný účinek operace přetažení závisí na tom, jak v aplikaci napsat příslušný kód.  
  
 Cíl přetažení může například specifikovat, že vlivem přesunu dat na je přesouvání dat. Chcete-li však přesunout data, musí být přidána do cílového prvku a odebrán ze zdrojového elementu. Zdrojový element může indikovat, že umožňuje přesun dat, ale pokud neposkytnete kód pro odebrání dat ze zdrojového elementu, konečný výsledek bude zkopírován a nebude přesunut.  
  
<a name="Drag_and_Drop_Events"></a>
## <a name="drag-and-drop-events"></a>Události přetažení  
 Operace přetažení podporují model řízený událostmi.  Zdrojový zdroj i cíl přetažení používají ke zpracování operací přetažení standardní sadu událostí.  Následující tabulky shrnují standardní události přetažení myší. Jedná se o připojené události ke <xref:System.Windows.DragDrop> třídě. Další informace o připojených událostech najdete v tématu [Přehled připojených událostí](attached-events-overview.md).  
  
### <a name="drag-source-events"></a>Přetáhněte zdrojové události  
  
|Událost|Souhrn|  
|-----------|-------------|  
|<xref:System.Windows.DragDrop.GiveFeedback>|Tato událost probíhá nepřetržitě během operace přetažení a umožňuje zdroji přetažení poskytnout uživateli informace o zpětné vazbě. Tato zpětná vazba je obvykle dána změnou vzhledu ukazatele myši k označení efektů povolených cílem přetažení.  Toto je probublávání událost.|  
|<xref:System.Windows.DragDrop.QueryContinueDrag>|Tato událost nastane, když dojde ke změně v stavech tlačítek klávesnice nebo myši během operace přetažení a umožňuje, aby se zdroj přetažení zrušil v závislosti na stavu klíče nebo tlačítka. Toto je probublávání událost.|  
|<xref:System.Windows.DragDrop.PreviewGiveFeedback>|TUNELING verze <xref:System.Windows.DragDrop.GiveFeedback> .|  
|<xref:System.Windows.DragDrop.PreviewQueryContinueDrag>|TUNELING verze <xref:System.Windows.DragDrop.QueryContinueDrag> .|  
  
### <a name="drop-target-events"></a>Vyřadit cílové události  
  
|Událost|Souhrn|  
|-----------|-------------|  
|<xref:System.Windows.DragDrop.DragEnter>|Tato událost nastane, pokud je objekt přetažen do hranice cíle přetažení. Toto je probublávání událost.|  
|<xref:System.Windows.DragDrop.DragLeave>|Tato událost nastane, pokud je objekt přetažen mimo hranici cíle přetažení.  Toto je probublávání událost.|  
|<xref:System.Windows.DragDrop.DragOver>|Tato událost probíhá průběžně při přetahování objektu (přesunuto) v rámci hranice cílového umístění. Toto je probublávání událost.|  
|<xref:System.Windows.DragDrop.Drop>|Tato událost nastane, pokud je objekt v cíli přetažení vyřazen.  Toto je probublávání událost.|  
|<xref:System.Windows.DragDrop.PreviewDragEnter>|TUNELING verze <xref:System.Windows.DragDrop.DragEnter> .|  
|<xref:System.Windows.DragDrop.PreviewDragLeave>|TUNELING verze <xref:System.Windows.DragDrop.DragLeave> .|  
|<xref:System.Windows.DragDrop.PreviewDragOver>|TUNELING verze <xref:System.Windows.DragDrop.DragOver> .|  
|<xref:System.Windows.DragDrop.PreviewDrop>|TUNELING verze <xref:System.Windows.DragDrop.Drop> .|  
  
 Chcete-li zpracovat události přetažení pro instance objektu, přidejte obslužné rutiny pro události uvedené v předchozích tabulkách. Chcete-li zpracovat události přetažení na úrovni třídy, přepište odpovídající virtuální událost on * a \* metody PreviewEvent. Další informace naleznete v tématu [zpracování tříd směrovaných událostí pomocí ovládacích prvků základní třídy](marking-routed-events-as-handled-and-class-handling.md#Class_Handling_of_Routed_Events).  
  
<a name="Implementing_Drag_And_Drop"></a>
## <a name="implementing-drag-and-drop"></a>Implementace přetažení myší  
 Prvek uživatelského rozhraní může být zdroj přetažení, cíl přetažení nebo obojí. Chcete-li implementovat základní přetahování, napíšete kód pro zahájení operace přetažení a zpracování vyřazených dat. Můžete rozšířit možnosti přetahování pomocí zpracování volitelných událostí přetažení.  
  
 K implementaci základních přetahování budete provádět následující úlohy:  
  
- Identifikujte prvek, který bude zdrojem přetažení. Zdroj přetažení může být <xref:System.Windows.UIElement> nebo <xref:System.Windows.ContentElement> .  
  
- Vytvořte obslužnou rutinu události ve zdroji přetažení, který spustí operaci přetažení. Událost je obvykle <xref:System.Windows.UIElement.MouseMove> událost.  
  
- V obslužné rutině zdrojové události přetažením volejte <xref:System.Windows.DragDrop.DoDragDrop%2A> metodu pro zahájení operace přetažení. V <xref:System.Windows.DragDrop.DoDragDrop%2A> volání zadejte zdroj přetažení, data, která mají být přenesena, a povolené efekty.  
  
- Identifikujte prvek, který bude cílem přetažení. Cíl přetažení může být <xref:System.Windows.UIElement> nebo <xref:System.Windows.ContentElement> .  
  
- V poli cíl přetažení nastavte <xref:System.Windows.UIElement.AllowDrop%2A> vlastnost na hodnotu `true` .  
  
- V cíli přetažení vytvořte <xref:System.Windows.DragDrop.Drop> obslužnou rutinu události pro zpracování vyřazených dat.  
  
- V <xref:System.Windows.DragDrop.Drop> obslužné rutině události rozbalte data z pomocí <xref:System.Windows.DragEventArgs> <xref:System.Windows.DataObject.GetDataPresent%2A> <xref:System.Windows.DataObject.GetData%2A> metod a.  
  
- V <xref:System.Windows.DragDrop.Drop> obslužné rutině události použijte data k provedení požadované operace přetažení.  
  
 Implementaci přetahování můžete vylepšit vytvořením vlastní <xref:System.Windows.DataObject> a zpracováním volitelných událostí pro přetažení zdroje a přetažením, jak je znázorněno v následujících úlohách:  
  
- Chcete-li přenést vlastní data nebo více datových položek, vytvořte objekt, <xref:System.Windows.DataObject> který bude předána <xref:System.Windows.DragDrop.DoDragDrop%2A> metodě.  
  
- Chcete-li provést další akce během přetahování, <xref:System.Windows.DragDrop.DragEnter> zpracujte <xref:System.Windows.DragDrop.DragOver> události, a <xref:System.Windows.DragDrop.DragLeave> v cíli přetažení.  
  
- Chcete-li změnit vzhled ukazatele myši, zpracujte <xref:System.Windows.DragDrop.GiveFeedback> událost ve zdroji přetažení.  
  
- Chcete-li změnit způsob zrušení operace přetažení, zpracujte <xref:System.Windows.DragDrop.QueryContinueDrag> událost na zdroj přetažení.  
  
<a name="Drag_And_Drop_Example"></a>
## <a name="drag-and-drop-example"></a>Příklad přetahování myší  
 Tato část popisuje, jak implementovat funkci přetažení pro <xref:System.Windows.Shapes.Ellipse> element. <xref:System.Windows.Shapes.Ellipse>Je jak zdroj přetažení, tak i cíl přetažení. Přenesená data jsou řetězcová reprezentace vlastnosti elipsy <xref:System.Windows.Shapes.Shape.Fill%2A> . Následující kód XAML ukazuje <xref:System.Windows.Shapes.Ellipse> prvek a události související s přetahováním, které zpracovávají. Úplný postup, jak implementovat přetahování, najdete v tématu [Návod: povolení přetahování na uživatelském ovládacím prvku](walkthrough-enabling-drag-and-drop-on-a-user-control.md).  
  
 [!code-xaml[DragDropSnippets#EllipseXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml#ellipsexaml)]  
  
### <a name="enabling-an-element-to-be-a-drag-source"></a>Povolení prvku jako zdroje přetažení  
 Objekt, který je zdrojem přetažení, zodpovídá za:  
  
- Určení, kdy dojde k přetahování.  
  
- Zahajuje se operace přetažení.  
  
- Identifikují se data, která se mají přenést.  
  
- Určení vlivu operace přetažení na přenášená data.  
  
 Zdroj přetažení může také uživateli poskytnout zpětnou vazbu týkající se povolených akcí (přesunutí, kopírování, žádné) a může zrušit operaci přetažení na základě dalšího vstupu uživatele, například při stisknutí klávesy ESC během tažení.  
  
 Je zodpovědností vaší aplikace na určení, kdy dojde k přetahování, a následnou inicializací operace přetažení voláním <xref:System.Windows.DragDrop.DoDragDrop%2A> metody. Obvykle se jedná o případ, kdy při <xref:System.Windows.UIElement.MouseMove> stisknutí tlačítka myši dojde k události nad prvkem, který se má přetáhnout. Následující příklad ukazuje, jak iniciovat operaci přetažení z <xref:System.Windows.UIElement.MouseMove> obslužné rutiny události <xref:System.Windows.Shapes.Ellipse> elementu, aby byla přetažena na zdroj. Přenesená data jsou řetězcová reprezentace vlastnosti elipsy <xref:System.Windows.Shapes.Shape.Fill%2A> .  
  
 [!code-csharp[DragDropSnippets#DoDragDrop](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#dodragdrop)]
 [!code-vb[DragDropSnippets#DoDragDrop](~/samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#dodragdrop)]  
  
 Uvnitř <xref:System.Windows.UIElement.MouseMove> obslužné rutiny události zavolejte <xref:System.Windows.DragDrop.DoDragDrop%2A> metodu pro zahájení operace přetažení. <xref:System.Windows.DragDrop.DoDragDrop%2A>Metoda přijímá tři parametry:  
  
- `dragSource`– Odkaz na objekt závislosti, který je zdrojem přenesených dat; To je obvykle zdrojem <xref:System.Windows.UIElement.MouseMove> události.  
  
- `data`– Objekt, který obsahuje přenesená data zabalená do <xref:System.Windows.DataObject> .  
  
- `allowedEffects`-Jedna z <xref:System.Windows.DragDropEffects> hodnot výčtu, která určuje povolené účinky operace přetažení.  
  
 Libovolný serializovatelný objekt lze předat v `data` parametru. Pokud data ještě nejsou zabalená do a, automaticky se zabalí <xref:System.Windows.DataObject> do nového <xref:System.Windows.DataObject> . Chcete-li předat více datových položek, je nutné vytvořit <xref:System.Windows.DataObject> sami sebe a předat ji <xref:System.Windows.DragDrop.DoDragDrop%2A> metodě. Další informace najdete v tématu [data a datové objekty](data-and-data-objects.md).  
  
 `allowedEffects`Parametr se používá k určení toho, jak bude zdroj přetažení umožňovat přenesené data. Společné hodnoty pro zdroj přetažení jsou <xref:System.Windows.DragDropEffects.Copy> , <xref:System.Windows.DragDropEffects.Move> a <xref:System.Windows.DragDropEffects.All> .  
  
> [!NOTE]
> Cíl přetažení také umožňuje určit, jaké účinky má v reakci na Vyřazená data. Například pokud cíl přetažení nerozpozná datový typ, který má být vyřazen, může odmítat data nastavením povolených efektů na <xref:System.Windows.DragDropEffects.None> . Obvykle to dělá v <xref:System.Windows.DragDrop.DragOver> obslužné rutině události.  
  
 Zdroj přetažení může volitelně zpracovávat <xref:System.Windows.DragDrop.GiveFeedback> události a <xref:System.Windows.DragDrop.QueryContinueDrag> . Tyto události mají výchozí obslužné rutiny, které se používají, pokud události neoznačíte jako zpracovávané. Tyto události obvykle budete ignorovat, pokud nemáte konkrétní nutnost změnit jejich výchozí chování.  
  
 <xref:System.Windows.DragDrop.GiveFeedback>Událost je vyvolána průběžně při přetahování zdroje. Výchozí obslužná rutina této události kontroluje, zda je zdroj přetažení přes platný cíl přetažení. Pokud je, kontroluje povolené účinky cíle přetažení. Pak poskytne zpětné vazby koncovému uživateli týkající se povolených efektů odkládacího pole. To se obvykle provádí změnou ukazatele myši na kurzor bez přetažení, kopírování nebo přesunutí. Tuto událost byste měli zpracovat pouze v případě, že potřebujete použít vlastní kurzory k poskytnutí zpětné vazby uživateli. Pokud tuto událost pořídíte, nezapomeňte ji označit jako zpracovanou, aby výchozí obslužná rutina nepsala vaši obslužnou rutinu.  
  
 <xref:System.Windows.DragDrop.QueryContinueDrag>Událost je vyvolána průběžně při přetahování zdroje. Tuto událost můžete zpracovat a určit tak, která akce ukončí operaci přetažení na základě stavu kláves ESC, SHIFT, CTRL a ALT a také stavu tlačítek myši. Výchozí obslužná rutina pro tuto událost zruší operaci přetažení, pokud je stisknuta klávesa ESC, a když dojde k uvolnění tlačítka myši, data se zruší.  
  
> [!CAUTION]
> Tyto události jsou během operace přetažení vyvolány průběžně. Proto byste se měli vyhnout úlohám náročným na prostředky v obslužných rutinách událostí.  Například při každém vyvolání události použijte ukazatel v mezipaměti místo vytvoření nového kurzoru <xref:System.Windows.DragDrop.GiveFeedback> .  
  
### <a name="enabling-an-element-to-be-a-drop-target"></a>Povolení prvku jako cíle přetažení  
 Objekt, který je cílem přetažení, zodpovídá za:  
  
- Určení, že se jedná o platný cíl přetažení.  
  
- Reaguje na zdroj přetažení při přetahování přes cíl.  
  
- Kontrola, zda jsou přenesená data ve formátu, který může přijímat.  
  
- Zpracování vynechaných dat.  
  
 Chcete-li určit, že prvek je cílem přetažení, nastavte jeho <xref:System.Windows.UIElement.AllowDrop%2A> vlastnost na `true` . Události cíle přetažení budou následně vyvolány na prvek, aby bylo možné je zpracovat. Během operace přetažení dojde v cíli přetažení k následující posloupnosti událostí:  
  
1. <xref:System.Windows.DragDrop.DragEnter>  
  
2. <xref:System.Windows.DragDrop.DragOver>  
  
3. <xref:System.Windows.DragDrop.DragLeave> nebo <xref:System.Windows.DragDrop.Drop>  
  
 K <xref:System.Windows.DragDrop.DragEnter> události dojde, když jsou data přetažena do hranice cílového umístění. Tato událost se obvykle zpracovává, aby poskytovala náhled efektů operace přetažení, pokud je to vhodné pro vaši aplikaci. Nenastavte <xref:System.Windows.DragEventArgs.Effects%2A?displayProperty=nameWithType> vlastnost v <xref:System.Windows.DragDrop.DragEnter> události, jak bude přepsána v <xref:System.Windows.DragDrop.DragOver> události.  
  
 Následující příklad ukazuje <xref:System.Windows.DragDrop.DragEnter> obslužnou rutinu události pro <xref:System.Windows.Shapes.Ellipse> element. Tento kód zobrazí náhled efektů operace přetažení uložením aktuálního <xref:System.Windows.Shapes.Shape.Fill%2A> štětce. Potom používá <xref:System.Windows.DataObject.GetDataPresent%2A> metodu ke kontrole, zda je <xref:System.Windows.DataObject> přetaženo přes elipsu obsahující řetězcová data, která lze převést na <xref:System.Windows.Media.Brush> . V takovém případě se data extrahují pomocí <xref:System.Windows.DataObject.GetData%2A> metody. Pak se převede na <xref:System.Windows.Media.Brush> a použije na elipsu. Změna se vrátí v <xref:System.Windows.DragDrop.DragLeave> obslužné rutině události. Pokud data nelze převést na <xref:System.Windows.Media.Brush> , není provedena žádná akce.  
  
 [!code-csharp[DragDropSnippets#DragEnter](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#dragenter)]
 [!code-vb[DragDropSnippets#DragEnter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#dragenter)]  
  
 <xref:System.Windows.DragDrop.DragOver>Událost probíhá průběžně, zatímco data jsou přetažena přes cíl přetažení. Tato událost se spáruje s <xref:System.Windows.DragDrop.GiveFeedback> událostí ve zdroji přetažení. V <xref:System.Windows.DragDrop.DragOver> obslužné rutině události se obvykle používají <xref:System.Windows.DataObject.GetDataPresent%2A> metody a <xref:System.Windows.DataObject.GetData%2A> ke kontrole, zda jsou přenesená data ve formátu, který může cíl přetažení zpracovat. Můžete také ověřit, zda jsou stisknuty jakékoli modifikační klávesy, což obvykle indikuje, zda uživatel zamýšlí akci přesunutí nebo kopírování. Po provedení těchto kontrol nastavíte <xref:System.Windows.DragEventArgs.Effects%2A?displayProperty=nameWithType> vlastnost, aby upozornila na zdroj přetažení, který bude mít za následek odstranění dat. Zdroj přetažení obdrží tyto informace v argumentech <xref:System.Windows.DragDrop.GiveFeedback> události a může nastavit vhodný ukazatel na poskytnutí zpětné vazby uživateli.  
  
 Následující příklad ukazuje <xref:System.Windows.DragDrop.DragOver> obslužnou rutinu události pro <xref:System.Windows.Shapes.Ellipse> element. Tento kód zkontroluje, zda je <xref:System.Windows.DataObject> přetaženo na elipsu obsahující řetězcová data, která lze převést na <xref:System.Windows.Media.Brush> . Pokud ano, nastaví <xref:System.Windows.DragEventArgs.Effects%2A?displayProperty=nameWithType> vlastnost na hodnotu <xref:System.Windows.DragDropEffects.Copy> . To znamená, že zdroj přetažení je možné zkopírovat data do elipsy. Pokud data nelze převést na <xref:System.Windows.Media.Brush> , <xref:System.Windows.DragEventArgs.Effects%2A?displayProperty=nameWithType> vlastnost je nastavena na hodnotu <xref:System.Windows.DragDropEffects.None> . To označuje zdroj přetažení, že elipsa není platným cílem přetažení pro data.  
  
 [!code-csharp[DragDropSnippets#DragOver](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#dragover)]
 [!code-vb[DragDropSnippets#DragOver](~/samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#dragover)]  
  
 K <xref:System.Windows.DragDrop.DragLeave> události dojde, když jsou data přetažena mimo hranici cíle bez vyřazení. Tato událost se zpracovává za účelem vrácení všeho, co jste provedli v <xref:System.Windows.DragDrop.DragEnter> obslužné rutině události.  
  
 Následující příklad ukazuje <xref:System.Windows.DragDrop.DragLeave> obslužnou rutinu události pro <xref:System.Windows.Shapes.Ellipse> element. Tento kód vrátí náhled provedený v <xref:System.Windows.DragDrop.DragEnter> obslužné rutině události použitím uloženého <xref:System.Windows.Media.Brush> na tři tečky.  
  
 [!code-csharp[DragDropSnippets#DragLeave](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#dragleave)]
 [!code-vb[DragDropSnippets#DragLeave](~/samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#dragleave)]  
  
 K <xref:System.Windows.DragDrop.Drop> události dojde, když jsou data vyřazena přes cíl přetažení; ve výchozím nastavení k tomu dojde po uvolnění tlačítka myši. V <xref:System.Windows.DragDrop.Drop> obslužné rutině události použijte <xref:System.Windows.DataObject.GetData%2A> metodu k extrakci přenesených dat z <xref:System.Windows.DataObject> a proveďte jakékoli zpracování dat, které vaše aplikace vyžaduje. <xref:System.Windows.DragDrop.Drop>Událost ukončí operaci přetažení.  
  
 Následující příklad ukazuje <xref:System.Windows.DragDrop.Drop> obslužnou rutinu události pro <xref:System.Windows.Shapes.Ellipse> element. Tento kód používá účinky operace přetažení a je podobný kódu v <xref:System.Windows.DragDrop.DragEnter> obslužné rutině události. Kontroluje, zda je <xref:System.Windows.DataObject> přetaženo přes elipsu obsahující řetězcová data, která lze převést na <xref:System.Windows.Media.Brush> . V takovém případě <xref:System.Windows.Media.Brush> se použije na tři tečky. Pokud data nelze převést na <xref:System.Windows.Media.Brush> , není provedena žádná akce.  
  
 [!code-csharp[DragDropSnippets#Drop](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#drop)]
 [!code-vb[DragDropSnippets#Drop](~/samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#drop)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Clipboard>
- [Návod: Povolení přetahování pomocí myši na uživatelském ovládacím prvku](walkthrough-enabling-drag-and-drop-on-a-user-control.md)
- [– postupy](drag-and-drop-how-to-topics.md)
- [Přetažení](drag-and-drop.md)
