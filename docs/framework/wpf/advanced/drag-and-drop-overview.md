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
ms.openlocfilehash: dd42af77300a7a93bbcbfa4c8f1fc365fc3f5da1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185991"
---
# <a name="drag-and-drop-overview"></a>Přehled přetažení
Toto téma obsahuje přehled podpory přetažením v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikacích. Přetažením obvykle odkazuje na metodu přenosu dat, která zahrnuje použití myši (nebo jiného polohovacího zařízení) k výběru jednoho [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]nebo více objektů, přetažení těchto objektů přes požadovaný cíl přetažení v aplikaci a jejich přetažení.  

<a name="Drag_and_Drop_Support"></a>
## <a name="drag-and-drop-support-in-wpf"></a>Podpora přetažení v WPF  
 Operace přetažení obvykle zahrnují dvě strany: zdroj přetažení, ze kterého pochází přetažený objekt, a cíl přetažení, který přijímá vynechaný objekt.  Zdroj přetažení a cíl přetažení může být prvky uživatelského rozhraní ve stejné aplikaci nebo jiné aplikace.  
  
 Typ a počet objektů, se kterými lze manipulovat přetažením a přetažením, je zcela libovolný. Například soubory, složky a výběry obsahu jsou některé z běžnějších objektů, s nimiž se manipuluje pomocí operací přetažení myší.  
  
 Konkrétní akce prováděné během operace přetažení maže jsou specifické pro aplikaci a často jsou určeny kontextem.  Například přetažením výběru souborů z jedné složky do druhé na stejném paměťovém zařízení se soubory ve výchozím nastavení posune, zatímco přetažení souborů ze sdílené složky UNC (Un) do místní složky soubory ve výchozím nastavení zkopíruje.  
  
 Drag-and-drop zařízení poskytované [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jsou navrženy tak, aby byly vysoce flexibilní a přizpůsobitelné pro podporu široké škály drag-and-drop scénáře.  Přetažení mandatorní ho podporuje manipulaci s objekty v rámci jedné aplikace nebo mezi různými aplikacemi. Přetahování mezi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacemi a jinými aplikacemi systému Windows je také plně podporováno.  
  
 V [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]souboru <xref:System.Windows.ContentElement> se může přetáhnout nebo <xref:System.Windows.UIElement> se ho zúčastnit. Události a metody požadované pro operace přetažení maže jsou definovány ve <xref:System.Windows.DragDrop> třídě. <xref:System.Windows.UIElement> Třídy <xref:System.Windows.ContentElement> a obsahují aliasy pro <xref:System.Windows.DragDrop> připojené události tak, aby se <xref:System.Windows.UIElement> události <xref:System.Windows.ContentElement> zobrazily v seznamu členů třídy, když nebo je zděděn jako základní prvek. Obslužné rutiny událostí, které jsou <xref:System.Windows.DragDrop> připojeny k těmto událostem, jsou připojeny k podkladové připojené události a obdrží stejnou instanci dat události. Další informace naleznete <xref:System.Windows.UIElement.Drop?displayProperty=nameWithType> na události.  
  
> [!IMPORTANT]
> Ole přetažení nefunguje v zóně Internet.  
  
<a name="Data_Transfer"></a>
## <a name="data-transfer"></a>Přenos dat  
 Přetažení je součástí obecnější oblasti přenosu dat. Přenos dat zahrnuje operace přetažení a kopírování a vkládání. Operace přetažení myší je obdobou operace kopírování a vkládání nebo vyjmutí a vložení, která se používá k přenosu dat z jednoho objektu nebo aplikace do jiného pomocí systémové schránky. Oba typy operací vyžadují:  
  
- Zdrojový objekt, který poskytuje data.  
  
- Způsob dočasného uložení přenesených dat.  
  
- Cílový objekt, který přijímá data.  
  
 Při kopírování a vkládání se systémová schránka používá k dočasnému uložení přenesených dat. v operaci přetažení se <xref:System.Windows.DataObject> používá k ukládání dat. Koncepčně datový objekt se skládá z jednoho <xref:System.Object> nebo více párů, který obsahuje skutečná data a odpovídající identifikátor formátu dat.  
  
 Zdroj přetažení zahájí operaci přetažení voláním statické <xref:System.Windows.DragDrop.DoDragDrop%2A?displayProperty=nameWithType> metody a předáním přenesených dat. Metoda <xref:System.Windows.DragDrop.DoDragDrop%2A> bude automaticky zalomit <xref:System.Windows.DataObject> data v případě potřeby. Pro větší kontrolu nad formátem dat, můžete <xref:System.Windows.DataObject> zabalit data <xref:System.Windows.DragDrop.DoDragDrop%2A> před předáním do metody. Cíl přetažení je zodpovědný za extrahování dat z <xref:System.Windows.DataObject>. Další informace o práci s datovými objekty naleznete v [tématu Data and Data Objects](data-and-data-objects.md).  
  
 Zdroj a cíl operace přetažení maže jsou prvky uživatelského rozhraní; data, která je ve skutečnosti přenášena, však obvykle nemá vizuální reprezentaci. Můžete napsat kód poskytnout vizuální reprezentaci dat, která je přetažena, jako například dochází při přetahování souborů v Průzkumníkovi Windows. Ve výchozím nastavení je uživateli poskytnuta zpětná vazba změnou kurzoru tak, aby představoval efekt, který bude mít operace přetažení na data, například zda budou data přesunuta nebo zkopírována.  
  
### <a name="drag-and-drop-effects"></a>Efekty přetažení myší  
 Operace přetažení může mít různé účinky na přenesená data. Můžete například zkopírovat data nebo je můžete přesunout. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]definuje <xref:System.Windows.DragDropEffects> výčet, který můžete použít k určení efektu operace přetažení myší. Ve zdroji přetažení můžete určit efekty, které <xref:System.Windows.DragDrop.DoDragDrop%2A> zdroj v metodě povolí. V cílové přetažení můžete určit efekt, který <xref:System.Windows.DragEventArgs.Effects%2A> cíl zamýšlí ve vlastnosti třídy. <xref:System.Windows.DragEventArgs> Když cíl přetažení určuje jeho <xref:System.Windows.DragDrop.DragOver> zamýšlený účinek v případě, že informace <xref:System.Windows.DragDrop.GiveFeedback> je předána zpět do zdroje přetažení v události. Zdroj přetažení používá tyto informace k informování uživatele, jaký vliv má cíl přetažení mít na data. Při přetažení dat cíl přetažení určuje jeho <xref:System.Windows.DragDrop.Drop> skutečný účinek v události. Tyto informace jsou předány zpět do zdroje <xref:System.Windows.DragDrop.DoDragDrop%2A> přetažení jako vrácená hodnota metody. Pokud cíl přetažení vrátí efekt, který není `allowedEffects`v seznamu zdrojů přetažení , operace přetažení je zrušena bez přenosu dat.  
  
 Je důležité si uvědomit, že v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.DragDropEffects> aplikaci se hodnoty používají pouze k zajištění komunikace mezi zdrojem přetažení a cílem přetažení, pokud jde o účinky operace přetažení myší. Skutečný efekt operace přetažení závisí na zápisu příslušného kódu v aplikaci.  
  
 Cíl přetažení může například určit, že efekt uvolněním dat na něj je přesunout data. Chcete-li však přesunout data, musí být přidána do cílového prvku a odebrána ze zdrojového prvku. Zdrojový prvek může znamenat, že umožňuje přesunutí dat, ale pokud nezadáte kód k odebrání dat ze zdrojového prvku, konečným výsledkem bude, že data jsou zkopírována a nejsou přesunuta.  
  
<a name="Drag_and_Drop_Events"></a>
## <a name="drag-and-drop-events"></a>Události přetažení  
 Operace přetažení podporují model řízený událostmi.  Zdroj přetažení i cíl přetažení používají standardní sadu událostí ke zpracování operací přetažení myší.  Následující tabulky shrnují standardní události přetažení myší. Jedná se o připojené <xref:System.Windows.DragDrop> události ve třídě. Další informace o připojených událostech naleznete v [tématu Přehled připojených událostí](attached-events-overview.md).  
  
### <a name="drag-source-events"></a>Přetažení zdrojových událostí  
  
|Událost|Souhrn|  
|-----------|-------------|  
|<xref:System.Windows.DragDrop.GiveFeedback>|K této události dochází nepřetržitě během operace přetažení a umožňuje zdroj přetažení poskytnout informace o zpětné vazbě pro uživatele. Tato zpětná vazba je obvykle dána změnou vzhledu ukazatele myši k označení efektů povolených cílem přetažení.  Tohle je bublající událost.|  
|<xref:System.Windows.DragDrop.QueryContinueDrag>|K této události dochází, když dojde ke změně stavu klávesnice nebo tlačítka myši během operace přetažení a umožňuje zdroj přetažení zrušit operaci přetažení mů e v závislosti na stavu klávesy nebo tlačítka. Tohle je bublající událost.|  
|<xref:System.Windows.DragDrop.PreviewGiveFeedback>|Tunelové propojení <xref:System.Windows.DragDrop.GiveFeedback>verze .|  
|<xref:System.Windows.DragDrop.PreviewQueryContinueDrag>|Tunelové propojení <xref:System.Windows.DragDrop.QueryContinueDrag>verze .|  
  
### <a name="drop-target-events"></a>Události cíle přetažení  
  
|Událost|Souhrn|  
|-----------|-------------|  
|<xref:System.Windows.DragDrop.DragEnter>|K této události dochází, když je objekt přetažen do hranice cíle přetažení. Tohle je bublající událost.|  
|<xref:System.Windows.DragDrop.DragLeave>|K této události dochází, když je objekt přetažen z hranice cíle přetažení.  Tohle je bublající událost.|  
|<xref:System.Windows.DragDrop.DragOver>|K této události dochází nepřetržitě, když je objekt přetažen (přesunut) v rámci hranice cíle přetažení. Tohle je bublající událost.|  
|<xref:System.Windows.DragDrop.Drop>|K této události dochází, když je objekt vynechán na cíl přetažení.  Tohle je bublající událost.|  
|<xref:System.Windows.DragDrop.PreviewDragEnter>|Tunelové propojení <xref:System.Windows.DragDrop.DragEnter>verze .|  
|<xref:System.Windows.DragDrop.PreviewDragLeave>|Tunelové propojení <xref:System.Windows.DragDrop.DragLeave>verze .|  
|<xref:System.Windows.DragDrop.PreviewDragOver>|Tunelové propojení <xref:System.Windows.DragDrop.DragOver>verze .|  
|<xref:System.Windows.DragDrop.PreviewDrop>|Tunelové propojení <xref:System.Windows.DragDrop.Drop>verze .|  
  
 Chcete-li zpracovat události přetažení pro instance objektu, přidejte obslužné rutiny pro události uvedené v předchozích tabulkách. Chcete-li zpracovat události přetažení na úrovni třídy, přepište\*odpovídající metody virtual On*Event a On PreviewEvent. Další informace naleznete [v tématu Class Handling of Routed Events by Control Base Classes](marking-routed-events-as-handled-and-class-handling.md#Class_Handling_of_Routed_Events).  
  
<a name="Implementing_Drag_And_Drop"></a>
## <a name="implementing-drag-and-drop"></a>Implementace přetažení myší  
 Prvek ui může být zdroj přetažení, cíl přetažení nebo obojí. Chcete-li implementovat základní přetažení, napište kód pro zahájení operace přetažení a zpracování vynechaných dat. Můžete vylepšit možnosti přetažení pomocí volitelných událostí přetažení.  
  
 Chcete-li implementovat základní přetažení myší, provedete následující úkoly:  
  
- Identifikujte prvek, který bude zdrojem přetažení. Zdroj přetažení může <xref:System.Windows.UIElement> být <xref:System.Windows.ContentElement>a nebo a .  
  
- Vytvořte obslužnou rutinu události ve zdroji přetahování, která zahájí operaci přetažení myší. Událost je obvykle <xref:System.Windows.UIElement.MouseMove> událost.  
  
- V obslužné rutině události zdroje přetažení volejte metodu <xref:System.Windows.DragDrop.DoDragDrop%2A> k zahájení operace přetažení myší. Ve <xref:System.Windows.DragDrop.DoDragDrop%2A> volání určete zdroj přetahování, data, která mají být přenesena, a povolené efekty.  
  
- Identifikujte prvek, který bude cíl přetažení. Cíl přetažení <xref:System.Windows.UIElement> může <xref:System.Windows.ContentElement>být nebo .  
  
- Na cíl přetažení <xref:System.Windows.UIElement.AllowDrop%2A> nastavte `true`vlastnost na .  
  
- V cíli přetažení <xref:System.Windows.DragDrop.Drop> vytvořte obslužnou rutinu události pro zpracování vyřazená data.  
  
- V <xref:System.Windows.DragDrop.Drop> obslužné rutině <xref:System.Windows.DragEventArgs> události <xref:System.Windows.DataObject.GetDataPresent%2A> extrahujte data z pomocí metody a. <xref:System.Windows.DataObject.GetData%2A>  
  
- V <xref:System.Windows.DragDrop.Drop> obslužné rutině události použijte data k provedení požadované operace přetažení myší.  
  
 Implementaci přetaženímůžete vylepšit vytvořením vlastního <xref:System.Windows.DataObject> a zpracováním volitelných událostí zdroje přetažení a přetažení, jak je znázorněno v následujících úkolech:  
  
- Chcete-li přenést vlastní data nebo <xref:System.Windows.DataObject> více datových položek, vytvořte metodu. <xref:System.Windows.DragDrop.DoDragDrop%2A>  
  
- Chcete-li během přetažení provést <xref:System.Windows.DragDrop.DragEnter> <xref:System.Windows.DragDrop.DragOver>další <xref:System.Windows.DragDrop.DragLeave> akce, zpracovat položku , a události v cílovém přetažení.  
  
- Chcete-li změnit vzhled ukazatele myši, zpracovat <xref:System.Windows.DragDrop.GiveFeedback> událost na zdroji přetažení.  
  
- Chcete-li změnit způsob zrušení operace přetažení, <xref:System.Windows.DragDrop.QueryContinueDrag> zpracovat událost na zdroji přetažení.  
  
<a name="Drag_And_Drop_Example"></a>
## <a name="drag-and-drop-example"></a>Příklad přetažení  
 Tato část popisuje, jak implementovat přetažení <xref:System.Windows.Shapes.Ellipse> prvku. Je <xref:System.Windows.Shapes.Ellipse> zdroj přetažení a cíl přetažení. Přenesená data jsou řetězcovou reprezentací vlastnosti elipsy. <xref:System.Windows.Shapes.Shape.Fill%2A> Následující XAML zobrazuje <xref:System.Windows.Shapes.Ellipse> prvek a události související s přetažením, které zpracovává. Úplné kroky k implementaci přetažení myší najdete v [tématu Návod: Povolení přetažení uživatelského ovládacího prvku](walkthrough-enabling-drag-and-drop-on-a-user-control.md).  
  
 [!code-xaml[DragDropSnippets#EllipseXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml#ellipsexaml)]  
  
### <a name="enabling-an-element-to-be-a-drag-source"></a>Povolení prvku jako zdroje přetažení  
 Objekt, který je zdrojem přetažení, je zodpovědný za:  
  
- Identifikace, kdy dojde k přetažení.  
  
- Zahajuji operaci přetažení myší.  
  
- Identifikace dat, která mají být přenesena.  
  
- Určení efektů, které může mít operace přetažení na přenesená data.  
  
 Zdroj přetažení může také poskytnout uživateli zpětnou vazbu ohledně povolených akcí (přesunutí, kopírování, žádné) a může zrušit operaci přetažení mj.  
  
 Je odpovědností aplikace určit, kdy dojde k přetažení a potom zahájit operaci přetažení voláním <xref:System.Windows.DragDrop.DoDragDrop%2A> metody. Obvykle se jedná o <xref:System.Windows.UIElement.MouseMove> událost, která nastane přes prvek, který má být přetažen při stisknutí tlačítka myši. Následující příklad ukazuje, jak zahájit operaci přetažení <xref:System.Windows.UIElement.MouseMove> z obslužné rutiny události <xref:System.Windows.Shapes.Ellipse> prvku, aby byl zdrojem přetažení. Přenesená data jsou řetězcovou reprezentací vlastnosti elipsy. <xref:System.Windows.Shapes.Shape.Fill%2A>  
  
 [!code-csharp[DragDropSnippets#DoDragDrop](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#dodragdrop)]
 [!code-vb[DragDropSnippets#DoDragDrop](~/samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#dodragdrop)]  
  
 Uvnitř obslužné <xref:System.Windows.UIElement.MouseMove> <xref:System.Windows.DragDrop.DoDragDrop%2A> rutiny události volejte metodu k zahájení operace přetažení myší. Metoda <xref:System.Windows.DragDrop.DoDragDrop%2A> má tři parametry:  
  
- `dragSource`– odkaz na objekt závislosti, který je zdrojem přenesených dat; to je obvykle zdrojem <xref:System.Windows.UIElement.MouseMove> události.  
  
- `data`- Objekt, který obsahuje přenesená data, <xref:System.Windows.DataObject>zabalené v .  
  
- `allowedEffects`- Jedna <xref:System.Windows.DragDropEffects> z hodnot výčtu, která určuje povolené účinky operace přetažení myší.  
  
 V parametru `data` lze předat libovolný serializovatelný objekt. Pokud data ještě nejsou zabalena <xref:System.Windows.DataObject>do , budou automaticky zabalena do nového <xref:System.Windows.DataObject>. Chcete-li předat více datových <xref:System.Windows.DataObject> položek, musíte vytvořit <xref:System.Windows.DragDrop.DoDragDrop%2A> sami a předat ji metodě. Další informace naleznete v [tématu Data and Data Objects](data-and-data-objects.md).  
  
 Parametr `allowedEffects` se používá k určení, co zdroj přetažení umožní cíl přetažení dělat s přenesenými daty. Běžné hodnoty zdroje přetažení <xref:System.Windows.DragDropEffects.Copy> <xref:System.Windows.DragDropEffects.Move>jsou <xref:System.Windows.DragDropEffects.All>, a .  
  
> [!NOTE]
> Cíl přetažení je také schopen určit, jaké účinky má v úmyslu v reakci na vynecháná data. Například pokud cíl přetažení nerozpozná datový typ, který má být vynechán, může <xref:System.Windows.DragDropEffects.None>odmítnout data nastavením povolených efektů na . Obvykle to provádí v <xref:System.Windows.DragDrop.DragOver> jeho obslužné rutině události.  
  
 Zdroj přetažení může <xref:System.Windows.DragDrop.GiveFeedback> volitelně <xref:System.Windows.DragDrop.QueryContinueDrag> zpracovat události a. Tyto události mají výchozí obslužné rutiny, které se používají, pokud neoznačíte události jako zpracované. Obvykle budete ignorovat tyto události, pokud máte konkrétní potřebu změnit jejich výchozí chování.  
  
 Událost <xref:System.Windows.DragDrop.GiveFeedback> je vyvolána nepřetržitě při přetahování zdroje. Výchozí obslužná rutina pro tuto událost kontroluje, zda je zdroj přetažení nad platným cílem přetažení. Pokud ano, zkontroluje povolené účinky cíle přetažení. To pak dává zpětnou vazbu koncovému uživateli, pokud jde o povolené efekty přetažení. To se obvykle provádí změnou kurzoru myši na kurzor bez přetažení, kopírování nebo přesunutí kurzoru. Tuto událost byste měli zpracovat pouze v případě, že potřebujete použít vlastní kurzory k poskytnutí zpětné vazby uživateli. Pokud zpracováváte tuto událost, nezapomeňte ji označit jako zpracovat tak, aby výchozí obslužná rutina nepřepsána obslužná rutina.  
  
 Událost <xref:System.Windows.DragDrop.QueryContinueDrag> je vyvolána nepřetržitě při přetahování zdroje. Tuto událost můžete zpracovat a určit, jaká akce ukončí operaci přetažením na základě stavu kláves ESC, SHIFT, CTRL a ALT a stavu tlačítek myši. Výchozí obslužná rutina pro tuto událost zruší operaci přetažením, pokud je stisknuta klávesa ESC, a při uvolnění tlačítka myši klesne data.  
  
> [!CAUTION]
> Tyto události jsou vyvolány nepřetržitě během operace přetažení myší. Proto byste se měli vyhnout úlohám náročným na prostředky v obslužných rutinách událostí.  Například použijte kurzor uložený v mezipaměti namísto vytvoření nového kurzoru při každém vyvolání <xref:System.Windows.DragDrop.GiveFeedback> události.  
  
### <a name="enabling-an-element-to-be-a-drop-target"></a>Povolení prvku jako cíl přetažení  
 Objekt, který je cíl přetažení je zodpovědný za:  
  
- Určení, že se jedná o platný cíl přetažení.  
  
- Odpovídá na zdroj přetažení, když se přetáhne přes cíl.  
  
- Kontrola, zda jsou přenesená data ve formátu, který mohou přijímat.  
  
- Zpracování vynechaná data.  
  
 Chcete-li určit, že prvek je <xref:System.Windows.UIElement.AllowDrop%2A> cíl `true`přetažení, nastavte jeho vlastnost . Cílové události přetažení pak budou vyvolány na prvek, takže je můžete zpracovat. Během operace přetažení dojde k následující posloupnost událostí dochází na cíl přetažení:  
  
1. <xref:System.Windows.DragDrop.DragEnter>  
  
2. <xref:System.Windows.DragDrop.DragOver>  
  
3. <xref:System.Windows.DragDrop.DragLeave> nebo <xref:System.Windows.DragDrop.Drop>  
  
 K <xref:System.Windows.DragDrop.DragEnter> události dojde, když jsou data přetažena do hranice cíle přetažení. Obvykle zpracováváte tuto událost poskytnout náhled účinků operace přetažení myší, pokud je to vhodné pro vaši aplikaci. Nenastavovat <xref:System.Windows.DragEventArgs.Effects%2A?displayProperty=nameWithType> vlastnost <xref:System.Windows.DragDrop.DragEnter> v události, protože bude přepsána <xref:System.Windows.DragDrop.DragOver> v události.  
  
 Následující příklad ukazuje <xref:System.Windows.DragDrop.DragEnter> obslužnou rutinu <xref:System.Windows.Shapes.Ellipse> události pro prvek. Tento kód zobrazí náhled účinků operace přetažení myší uložením aktuální <xref:System.Windows.Shapes.Shape.Fill%2A> stopy. Poté použije <xref:System.Windows.DataObject.GetDataPresent%2A> metodu ke <xref:System.Windows.DataObject> kontrole, zda přetahovaná přes elipsu obsahuje řetězcová data, která lze převést na <xref:System.Windows.Media.Brush>. Pokud ano, data jsou extrahována <xref:System.Windows.DataObject.GetData%2A> pomocí metody. Potom je převeden na <xref:System.Windows.Media.Brush> a a použít na elipsu. Změna je vrácena v <xref:System.Windows.DragDrop.DragLeave> obslužné rutině události. Pokud data nelze převést <xref:System.Windows.Media.Brush>na , nebude provedena žádná akce.  
  
 [!code-csharp[DragDropSnippets#DragEnter](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#dragenter)]
 [!code-vb[DragDropSnippets#DragEnter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#dragenter)]  
  
 K <xref:System.Windows.DragDrop.DragOver> události dochází nepřetržitě, zatímco data jsou přetažena přes cíl přetažení. Tato událost je <xref:System.Windows.DragDrop.GiveFeedback> spárována s událostí ve zdroji přetahování. V <xref:System.Windows.DragDrop.DragOver> obslužné rutině <xref:System.Windows.DataObject.GetDataPresent%2A> <xref:System.Windows.DataObject.GetData%2A> události obvykle používáte metody a ke kontrole, zda jsou přenesená data ve formátu, který může cíl přetažení zpracovat. Můžete také zkontrolovat, zda jsou stisknuty všechny modifikační klávesy, což obvykle označuje, zda uživatel zamýšlí přesunout nebo kopírovat akci. Po provedení těchto kontrol nastavíte <xref:System.Windows.DragEventArgs.Effects%2A?displayProperty=nameWithType> vlastnost tak, aby upozorňovala zdroj přetahování, jaký vliv bude mít uvolnění dat. Zdroj přetažení obdrží tyto <xref:System.Windows.DragDrop.GiveFeedback> informace v události args a může nastavit odpovídající kurzor poskytnout zpětnou vazbu pro uživatele.  
  
 Následující příklad ukazuje <xref:System.Windows.DragDrop.DragOver> obslužnou rutinu <xref:System.Windows.Shapes.Ellipse> události pro prvek. Tento kód zkontroluje, <xref:System.Windows.DataObject> zda přetahovaná přes elipsu obsahuje řetězcová <xref:System.Windows.Media.Brush>data, která lze převést na . Pokud ano, nastaví <xref:System.Windows.DragEventArgs.Effects%2A?displayProperty=nameWithType> <xref:System.Windows.DragDropEffects.Copy>vlastnost na . To znamená, že zdroj přetažení, že data mohou být zkopírovány do elipsy. Pokud data nelze převést <xref:System.Windows.Media.Brush>na <xref:System.Windows.DragEventArgs.Effects%2A?displayProperty=nameWithType> , je <xref:System.Windows.DragDropEffects.None>vlastnost nastavena na . To znamená, že zdroj přetažení, že elipsa není platný cíl přetažení pro data.  
  
 [!code-csharp[DragDropSnippets#DragOver](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#dragover)]
 [!code-vb[DragDropSnippets#DragOver](~/samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#dragover)]  
  
 K <xref:System.Windows.DragDrop.DragLeave> události dochází, když jsou data přetažena z hranice cíle bez vynechání. Tuto událost zpracovat vrátit vše, co <xref:System.Windows.DragDrop.DragEnter> jste provedli v obslužné rutině události.  
  
 Následující příklad ukazuje <xref:System.Windows.DragDrop.DragLeave> obslužnou rutinu <xref:System.Windows.Shapes.Ellipse> události pro prvek. Tento kód vrátit náhled provedené <xref:System.Windows.DragDrop.DragEnter> v obslužné rutině události použitím uložené <xref:System.Windows.Media.Brush> na elipsu.  
  
 [!code-csharp[DragDropSnippets#DragLeave](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#dragleave)]
 [!code-vb[DragDropSnippets#DragLeave](~/samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#dragleave)]  
  
 K <xref:System.Windows.DragDrop.Drop> události dojde, když jsou data vynechána nad cílem přetažení; ve výchozím nastavení k tomu dochází při uvolnění tlačítka myši. V <xref:System.Windows.DragDrop.Drop> obslužné <xref:System.Windows.DataObject.GetData%2A> rutině události použijete metodu k extrahování přenesených dat z <xref:System.Windows.DataObject> a provedení zpracování dat, které vaše aplikace vyžaduje. Událost <xref:System.Windows.DragDrop.Drop> ukončí operaci přetažení myší.  
  
 Následující příklad ukazuje <xref:System.Windows.DragDrop.Drop> obslužnou rutinu <xref:System.Windows.Shapes.Ellipse> události pro prvek. Tento kód používá účinky operace přetažení a je podobný kódu v <xref:System.Windows.DragDrop.DragEnter> obslužné rutině události. Zkontroluje, zda <xref:System.Windows.DataObject> přetahovaná přes elipsu obsahuje řetězcová data, <xref:System.Windows.Media.Brush>která lze převést na . Pokud ano, <xref:System.Windows.Media.Brush> je aplikován na elipsu. Pokud data nelze převést <xref:System.Windows.Media.Brush>na , nebude provedena žádná akce.  
  
 [!code-csharp[DragDropSnippets#Drop](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#drop)]
 [!code-vb[DragDropSnippets#Drop](~/samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#drop)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Clipboard>
- [Návod: Povolení přetahování pomocí myši na uživatelském ovládacím prvku](walkthrough-enabling-drag-and-drop-on-a-user-control.md)
- [Témata s postupy](drag-and-drop-how-to-topics.md)
- [Přetažení](drag-and-drop.md)
