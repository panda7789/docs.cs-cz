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
ms.openlocfilehash: 2b76c8fd3e2c6961b6ebdddc9b7ff9649f5196f4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62051634"
---
# <a name="drag-and-drop-overview"></a>Přehled přetažení
Toto téma poskytuje přehled podpory přetažení myší v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikací. Přetáhněte myší obvykle odkazuje na metodu přenosu dat, která zahrnuje pomocí myši (nebo jiné polohovací zařízení) a vyberte jeden nebo více objektů, tyto objekty přetáhnete přes některé požadovaný cíl v [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]a jejich vyřazení.  

<a name="Drag_and_Drop_Support"></a>   
## <a name="drag-and-drop-support-in-wpf"></a>Podpora přetažení myší v subsystému WPF  
 Operace přetažení myší obvykle zahrnuje obě strany: přetáhněte zdroj, ze které pochází přetažený objekt a cíl přetažení, která přijímá přetažený objekt.  Cíl přetažení zdroje a drop může být prvky uživatelského rozhraní ve stejné aplikaci nebo jiné aplikaci.  
  
 Je zcela libovolného typu a počtu objektů, které lze ovládat pomocí přetahování myší. Například soubory, složky a výběr obsahu jsou některé z běžnějších objektů manipulovat prostřednictvím operací přetažení myší.  
  
 Konkrétní akce prováděné během operace přetažení myší jsou aplikace konkrétní a často určeného kontextu.  Například přetažení výběru souborů z jedné složky do jiné na stejném paměťovém zařízení přesune soubory ve výchozím nastavení, že přetáhnete soubory z [!INCLUDE[TLA#tla_unc](../../../../includes/tlasharptla-unc-md.md)] sdílenou složku do místní složky zkopíruje soubory ve výchozím nastavení.  
  
 Přetáhněte myší poskytované systémem [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jsou navržena jako vysoce flexibilní a přizpůsobitelné pro podporu široké škály scénářů a přetažení.  Manipulace s objekty v rámci jedné aplikace nebo mezi různými aplikacemi podporuje přetahování myší. Přetahování a uvolnění mezi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikací a dalších aplikací Windows je taky plně podporovaná.  
  
 V [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], všechny <xref:System.Windows.UIElement> nebo <xref:System.Windows.ContentElement> mohl podílet na přetahování myší. Události a metody potřebné pro operace přetažení myší jsou definovány v <xref:System.Windows.DragDrop> třídy. <xref:System.Windows.UIElement> a <xref:System.Windows.ContentElement> třídy obsahovat aliasy pro <xref:System.Windows.DragDrop> připojených událostí tak, aby události se zobrazí ve třídě členy seznamu, když <xref:System.Windows.UIElement> nebo <xref:System.Windows.ContentElement> dědí jako základní prvek. Obslužné rutiny událostí, které jsou připojené k těmto událostem, které jsou připojeny k podkladovým <xref:System.Windows.DragDrop> připojených událostí a příjem stejné instance dat události. Další informace naleznete v události <xref:System.Windows.UIElement.Drop?displayProperty=nameWithType>.  
  
> [!IMPORTANT]
>  OLE – přetažením nefunguje v zóně Internet.  
  
<a name="Data_Transfer"></a>   
## <a name="data-transfer"></a>Přenos dat  
 Přetažení myší je součástí obecnější části datové přenosy. Přenos dat zahrnuje operace přetažení myší a kopírování a vkládání. Operace přetažení myší je obdobou operaci kopírování a vkládání nebo vyjmutí a vložení, která se používá k přenosu dat z jednoho objektu nebo aplikace do jiné podle použití schránky systému. Vyžadují se oba typy operací:  
  
- Zdrojový objekt, který poskytuje data.  
  
- Způsob, jak dočasně ukládat přenášená data.  
  
- Cílový objekt, který přijímá data.  
  
 V operaci kopírování a vkládání do schránky systému se používá k dočasnému uložení přenášených dat; v rámci operace přetažení myší <xref:System.Windows.DataObject> se používá k uložení dat. Entity se skládá z jednoho nebo více párů datový objekt <xref:System.Object> obsahující skutečná data a odpovídající identifikátor formát data.  
  
 Zdroje přetažení zahájí operaci přetažení myší voláním statické <xref:System.Windows.DragDrop.DoDragDrop%2A?displayProperty=nameWithType> metoda a předáním přenášená data. <xref:System.Windows.DragDrop.DoDragDrop%2A> Metoda bude automaticky zalomí, data <xref:System.Windows.DataObject> v případě potřeby. Pro větší kontrolu nad formátem data, můžete data v zabalit <xref:System.Windows.DataObject> před předáním do <xref:System.Windows.DragDrop.DoDragDrop%2A> metody. Cíl přetažení je zodpovědný za extrahování dat z <xref:System.Windows.DataObject>. Další informace o práci s objekty dat, naleznete v tématu [Data a datové objekty](data-and-data-objects.md).  
  
 Zdroj a cíl operace přetažení myší jsou prvky uživatelského rozhraní; data, která je ve skutečnosti přenášených obvykle nemá vizuální reprezentace. Můžete napsat kód k poskytování vizuální znázornění dat, který je přetažen, jako například vyvolá se v případě přetahování souborů v Průzkumníku Windows. Ve výchozím nastavení zpětná vazba je uživateli poskytnutý změnou kurzor představují efekt, který bude mít operace přetažení myší na data, jako například, jestli budou data přesunout ani zkopírovat.  
  
### <a name="drag-and-drop-effects"></a>Účinky přetažení myší  
 Operace přetažení myší může mít různé účinky na přenášená data. Například můžete zkopírovat data nebo můžete přesunout data. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] definuje <xref:System.Windows.DragDropEffects> výčet, který můžete použít k určení efekt operace přetažení myší. Ve zdroji přetažení, můžete zadat efekty, které vám umožní zdroj v <xref:System.Windows.DragDrop.DoDragDrop%2A> metody. V cíl přetažení, můžete určit efekt, který si klade za cíl cíl v <xref:System.Windows.DragEventArgs.Effects%2A> vlastnost <xref:System.Windows.DragEventArgs> třídy. Určuje, kdy cíl přetažení zamýšlený účinek <xref:System.Windows.DragDrop.DragOver> události, které informace se předá zpět do zdroje přetáhněte v <xref:System.Windows.DragDrop.GiveFeedback> událostí. Zdroje přetažení používá tyto informace a informuje uživatele jaký vliv má cíl přetažení má v úmyslu mít na data. Při přetažení dat určuje cíl přetažení v jeho skutečné dopad <xref:System.Windows.DragDrop.Drop> událostí. Že informace je předán zpět do zdroje přetáhněte jako návratová hodnota <xref:System.Windows.DragDrop.DoDragDrop%2A> metody. Pokud cíl přetažení vrátí efekt, který není v seznamu zdrojů přetáhněte `allowedEffects`, přetáhněte myší operace se zrušila, bez přenosů dat, ke kterým dochází.  
  
 Je dobré si uvědomit, že v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], <xref:System.Windows.DragDropEffects> hodnoty se používají pouze k zajištění komunikace mezi přetáhněte zdroj a cíl přetažení o účincích operace přetažení myší. Skutečný výsledek operace přetažení myší, závisí na psaní příslušný kód ve vaší aplikaci.  
  
 Cíl přetažení mohou například určit, že efekt přetažení dat na něm je pro přesun dat. Ale pro přesun dat, musí být současně přidat do cílového elementu a odebrat ze zdrojového elementu. Source element může znamenat, že umožňuje přesun dat, ale pokud nezadáte kód a odeberte data ze zdrojového elementu, konečným výsledkem bude, že data jsou zkopírovány a nebyl přesunut.  
  
<a name="Drag_and_Drop_Events"></a>   
## <a name="drag-and-drop-events"></a>Události přetažení myší  
 Operace přetažení myší podporují s modelem řízené událostmi.  Přetáhněte zdroj a cíl operace přetažení myší pomocí standardní sadu událostí.  Následující tabulky shrnují standardní události přetažení myší. Toto jsou připojené události na <xref:System.Windows.DragDrop> třídy. Další informace o přidružené události najdete v tématu [přehled připojených událostí](attached-events-overview.md).  
  
### <a name="drag-source-events"></a>Zdroj události přetažení  
  
|Událost|Souhrn|  
|-----------|-------------|  
|<xref:System.Windows.DragDrop.GiveFeedback>|Tato událost neustále během operace přetažení myší a umožňuje zdroji přetažení poskytnout zpětnou vazbu informace pro uživatele. Tato zpětná vazba je tak, že změníte vzhled ukazatele myši běžně věnovat účincích dovolují cíl přetažení.  Toto je událost šíření.|  
|<xref:System.Windows.DragDrop.QueryContinueDrag>|Tato událost nastane, pokud dojde ke změně v klávesnici nebo tlačítka myši stavy během operace přetažení myší a umožňuje zdroji přetažení ke zrušení operace přetažení myší v závislosti na stavy klíč nebo tlačítka. Toto je událost šíření.|  
|<xref:System.Windows.DragDrop.PreviewGiveFeedback>|Tunelového propojení verzi <xref:System.Windows.DragDrop.GiveFeedback>.|  
|<xref:System.Windows.DragDrop.PreviewQueryContinueDrag>|Tunelového propojení verzi <xref:System.Windows.DragDrop.QueryContinueDrag>.|  
  
### <a name="drop-target-events"></a>Cíl události  
  
|Událost|Souhrn|  
|-----------|-------------|  
|<xref:System.Windows.DragDrop.DragEnter>|Tato událost vyvolá se při přetažení objektu do hranic cíl přetažení. Toto je událost šíření.|  
|<xref:System.Windows.DragDrop.DragLeave>|Tato událost nastane, pokud objekt ocitne mimo hranice cíl přetažení.  Toto je událost šíření.|  
|<xref:System.Windows.DragDrop.DragOver>|K této události dojde, nepřetržitě při přetažení objektu (přesunutý) v rámci hranice cíl přetažení. Toto je událost šíření.|  
|<xref:System.Windows.DragDrop.Drop>|Při přetažení objektu na cíl přetažení, dojde k této události.  Toto je událost šíření.|  
|<xref:System.Windows.DragDrop.PreviewDragEnter>|Tunelového propojení verzi <xref:System.Windows.DragDrop.DragEnter>.|  
|<xref:System.Windows.DragDrop.PreviewDragLeave>|Tunelového propojení verzi <xref:System.Windows.DragDrop.DragLeave>.|  
|<xref:System.Windows.DragDrop.PreviewDragOver>|Tunelového propojení verzi <xref:System.Windows.DragDrop.DragOver>.|  
|<xref:System.Windows.DragDrop.PreviewDrop>|Tunelového propojení verzi <xref:System.Windows.DragDrop.Drop>.|  
  
 Zpracování událostí a přetahování pro instancí objektu, přidejte obslužné rutiny pro události uvedené v předchozích tabulkách. Zpracování událostí a přetahování na úrovni třídy, přepište odpovídající virtuální na * událostí a na\*PreviewEvent metody. Další informace najdete v tématu [třídy zpracování směrování událostí, které ovládací prvek základní třídy](marking-routed-events-as-handled-and-class-handling.md#Class_Handling_of_Routed_Events).  
  
<a name="Implementing_Drag_And_Drop"></a>   
## <a name="implementing-drag-and-drop"></a>Implementace přetažení myší  
 Prvek uživatelského rozhraní může být přetáhněte zdroj nebo cíl přetažení. K implementaci základní přetažení myší, píšete kód k zahájení operace přetažení myší a zamítnuté data zpracovat. Přetáhněte myší prostředí můžete zvýšit, že zpracování události volitelné a přetažení.  
  
 K implementaci základní přetažení myší, se dokončí následující úkoly:  
  
- Prvek, který bude zdroji přetažení určete. Může být zdroji přetažení <xref:System.Windows.UIElement> nebo <xref:System.Windows.ContentElement>.  
  
- Vytvořte obslužnou rutinu události na zdroji přetažení, který opraví, zahájí se operace přetažení myší. Událost je obvykle <xref:System.Windows.UIElement.MouseMove> událostí.  
  
- V obslužné rutině události zdroje přetáhněte volání <xref:System.Windows.DragDrop.DoDragDrop%2A> metoda k zahájení operace přetažení myší. V <xref:System.Windows.DragDrop.DoDragDrop%2A> volání, zadejte zdroji přetažení, přenos dat a povolené efekty.  
  
- Identifikujte elementu, který bude cíl přetažení. Může být cíle přetažení <xref:System.Windows.UIElement> nebo <xref:System.Windows.ContentElement>.  
  
- Na cíl, nastavte <xref:System.Windows.UIElement.AllowDrop%2A> vlastnost `true`.  
  
- Vytvořte v cíl přetažení <xref:System.Windows.DragDrop.Drop> obslužná rutina události ke zpracování dat vyřazené.  
  
- V <xref:System.Windows.DragDrop.Drop> obslužná rutina události, extrahovat data <xref:System.Windows.DragEventArgs> pomocí <xref:System.Windows.DataObject.GetDataPresent%2A> a <xref:System.Windows.DataObject.GetData%2A> metody.  
  
- V <xref:System.Windows.DragDrop.Drop> obslužná rutina události, data použít k provedení požadované operace přetažení myší.  
  
 Implementace a přetahování můžete zvýšit tak, že vytvoříte vlastní <xref:System.Windows.DataObject> a zpracováním volitelné přetáhnout zdroje a drop cíl události, jak je znázorněno v následující úkoly:  
  
- Přenos vlastních dat nebo více datových položek, vytvoření <xref:System.Windows.DataObject> předat <xref:System.Windows.DragDrop.DoDragDrop%2A> metody.  
  
- Při přetažení provádět další akce, zpracování <xref:System.Windows.DragDrop.DragEnter>, <xref:System.Windows.DragDrop.DragOver>, a <xref:System.Windows.DragDrop.DragLeave> události na cíl přetažení.  
  
- Chcete-li změnit vzhled ukazatele myši, zpracovat <xref:System.Windows.DragDrop.GiveFeedback> události ve zdroji přetažení.  
  
- Chcete-li změnit, jak je zrušena operace přetažení myší, zpracovat <xref:System.Windows.DragDrop.QueryContinueDrag> události ve zdroji přetažení.  
  
<a name="Drag_And_Drop_Example"></a>   
## <a name="drag-and-drop-example"></a>Příklad přetažení myší  
 Tato část popisuje, jak implementovat a přetažení pro <xref:System.Windows.Shapes.Ellipse> elementu. <xref:System.Windows.Shapes.Ellipse> Přetáhněte zdroj a cíl přetažení. Přenášených dat je řetězcové vyjádření se třemi tečkami <xref:System.Windows.Shapes.Shape.Fill%2A> vlastnost. Zobrazí se následující XAML <xref:System.Windows.Shapes.Ellipse> element a související události přetažení myší, které zpracovává. Zopakujte kroky pro implementaci přetažení myší, naleznete v tématu [názorný postup: Povolení přetahování na uživatelský ovládací prvek](walkthrough-enabling-drag-and-drop-on-a-user-control.md).  
  
 [!code-xaml[DragDropSnippets#EllipseXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml#ellipsexaml)]  
  
### <a name="enabling-an-element-to-be-a-drag-source"></a>Umožňuje Element, který má jako zdroj přetažení  
 Objekt, který je zdrojem přetažení je zodpovědný za:  
  
- Identifikace, když dojde k přetáhněte.  
  
- Zahajuje se operace přetažení myší.  
  
- Identifikuje data, která mají být převedeny.  
  
- Určení efekty, které může mít na přenášených dat operace přetažení myší.  
  
 Zdroji přetažení může také váš názor na uživatele o povolených akcí (přesunout, kopírovat, none) a můžete zrušit operaci přetažení myší na základě zadání dalšího uživatele, například stisknutím klávesy ESC během tažení.  
  
 Je zodpovědností aplikace k určení, kdy dochází k přetáhněte, a poté operaci inicializovat přetažení myší pomocí volání <xref:System.Windows.DragDrop.DoDragDrop%2A> metody. Obvykle, když jde <xref:System.Windows.UIElement.MouseMove> přes elementu, který chcete přetáhnout, když se stiskne tlačítko myši, dojde k události. Následující příklad ukazuje, jak se zahájit operaci přetažení myší z <xref:System.Windows.UIElement.MouseMove> obslužná rutina události <xref:System.Windows.Shapes.Ellipse> element k němu zdroji přetažení. Přenášených dat je řetězcové vyjádření se třemi tečkami <xref:System.Windows.Shapes.Shape.Fill%2A> vlastnost.  
  
 [!code-csharp[DragDropSnippets#DoDragDrop](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#dodragdrop)]
 [!code-vb[DragDropSnippets#DoDragDrop](~/samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#dodragdrop)]  
  
 Uvnitř <xref:System.Windows.UIElement.MouseMove> obslužná rutina události, volání <xref:System.Windows.DragDrop.DoDragDrop%2A> metoda k zahájení operace přetažení myší. <xref:System.Windows.DragDrop.DoDragDrop%2A> Metoda přijímá tři parametry:  
  
- `dragSource` – Odkaz na objekt závislosti, které je zdrojem přenášených dat; Toto je obvykle zdroj <xref:System.Windows.UIElement.MouseMove> událostí.  
  
- `data` – Objekt, který obsahuje přenášených dat, který je obalen <xref:System.Windows.DataObject>.  
  
- `allowedEffects` -Jedním z <xref:System.Windows.DragDropEffects> hodnot výčtu, která určuje povolené efekty operace přetažení myší.  
  
 Může být jakýkoli serializovatelný objekt předaný `data` parametru. Je-li data již není zabalené v <xref:System.Windows.DataObject>, se automaticky uzavřou v novém <xref:System.Windows.DataObject>. Předat více položek dat, je nutné vytvořit <xref:System.Windows.DataObject> sami a předat ho metodě <xref:System.Windows.DragDrop.DoDragDrop%2A> metody. Další informace najdete v tématu [Data a datové objekty](data-and-data-objects.md).  
  
 `allowedEffects` Parametr se používá k určení, co se zdroji přetažení umožňují cíl přetažení se přenášená data. Běžné hodnoty pro zdroj přetažení <xref:System.Windows.DragDropEffects.Copy>, <xref:System.Windows.DragDropEffects.Move>, a <xref:System.Windows.DragDropEffects.All>.  
  
> [!NOTE]
>  Cíl přetažení je také určit jaké účinky se chystá v reakci na vynechaných data. Například, pokud cíl přetažení nedokáže rozpoznat datový typ, který chcete vyřadit, ho může odmítnout data nastavením jeho povolené efekty na <xref:System.Windows.DragDropEffects.None>. To obvykle provádí jeho <xref:System.Windows.DragDrop.DragOver> obslužné rutiny události.  
  
 Volitelně může zpracovat zdroji přetažení <xref:System.Windows.DragDrop.GiveFeedback> a <xref:System.Windows.DragDrop.QueryContinueDrag> události. Tyto události mají výchozích obslužných rutin, které se používají Pokud označíte události jako zpracování. Tyto události se obvykle ignorují, pokud nemáte konkrétní požadavky, chcete-li změnit jejich chování.  
  
 <xref:System.Windows.DragDrop.GiveFeedback> Událost se vyvolá, nepřetržitě, zatímco je přetažen zdroji přetažení. Výchozí obslužnou rutinu pro tuto událost, zkontroluje, zda zdroji přetažení přes cíle přetažení platný. Pokud se jedná, zkontroluje povolené efekty cíl přetažení. Poté přiřadí zpětné vazby pro koncového uživatele o účincích povolené přetažení. To se obvykle provádí změnou kurzoru myši na no pokles, kopírování nebo přesunutí kurzoru. Pokud musíte použít vlastní ukazatele k poskytnutí zpětné vazby pro uživatele, by měla pouze zpracování této události. Pokud tuto událost zpracujte, je nutné jej označte jako ošetřenou, takže výchozí obslužnou rutinu nepřepisuje obslužnou rutinu.  
  
 <xref:System.Windows.DragDrop.QueryContinueDrag> Událost se vyvolá, nepřetržitě, zatímco je přetažen zdroji přetažení. Dokáže zpracovat tuto událost, chcete-li zjistit, jaká akce se ukončí operaci přetažení myší podle stavu ESC, SHIFT, CTRL a ALT – klávesy, jakož i stav tlačítka myši. Výchozí obslužnou rutinu pro tuto událost zruší operaci přetažení myší, pokud stisknutí klávesy ESC a sníží data, pokud se uvolní tlačítko myši.  
  
> [!CAUTION]
>  Tyto události jsou vyvolány průběžně během operace přetažení myší. Proto byste se měli vyhnout náročné úkoly v obslužných rutinách událostí.  Použít místo vytvoření nového kurzor pokaždé, když například v mezipaměti kurzor <xref:System.Windows.DragDrop.GiveFeedback> událost se vyvolá.  
  
### <a name="enabling-an-element-to-be-a-drop-target"></a>Umožňuje Element, který má být cílem vyřadit  
 Objekt, který je cíl přetažení je zodpovědný za:  
  
- Určení, že se jedná platný cíl.  
  
- Reakce na zdroji přetažení, když ho přetáhne za cíl.  
  
- Ujistěte se, že přenášených dat ve formátu, který může přijímat.  
  
- Zpracování vynechaných data.  
  
 Chcete-li určit, že element je cíl přetažení, nastavíte její <xref:System.Windows.UIElement.AllowDrop%2A> vlastnost `true`. Události cíl přetažení pak bude vyvolána v elementu, aby bylo možné je zpracovat. Během operace přetažení myší dojde k následujícímu pořadí událostí na cíl přetažení:  
  
1. <xref:System.Windows.DragDrop.DragEnter>  
  
2. <xref:System.Windows.DragDrop.DragOver>  
  
3. <xref:System.Windows.DragDrop.DragLeave> Nebo <xref:System.Windows.DragDrop.Drop>  
  
 <xref:System.Windows.DragDrop.DragEnter> Události dojde, když data kvůli usnadnění použití vypsány hranici cíl přetažení. Tato událost ve verzi preview účinky operace přetažení myší, můžete obvykle zpracovávat ve v případě potřeby pro vaši aplikaci. Nenastavujte <xref:System.Windows.DragEventArgs.Effects%2A?displayProperty=nameWithType> vlastnost <xref:System.Windows.DragDrop.DragEnter> událost, protože se přepíše v <xref:System.Windows.DragDrop.DragOver> událostí.  
  
 Následující příklad ukazuje <xref:System.Windows.DragDrop.DragEnter> obslužné rutiny události pro <xref:System.Windows.Shapes.Ellipse> elementu. Tento kód zobrazí náhled účinky operace přetažení myší uložením aktuální <xref:System.Windows.Shapes.Shape.Fill%2A> štětce. Poté použije <xref:System.Windows.DataObject.GetDataPresent%2A> metodu ke kontrole, jestli <xref:System.Windows.DataObject> přetažen nad třemi tečkami obsahuje data řetězce, který lze převést na <xref:System.Windows.Media.Brush>. Pokud ano, je data extrahována pomocí <xref:System.Windows.DataObject.GetData%2A> metody. Je pak převedeno <xref:System.Windows.Media.Brush> a použít na tři tečky. Změny se vrátí zpět v <xref:System.Windows.DragDrop.DragLeave> obslužné rutiny události. Pokud data nelze převést na <xref:System.Windows.Media.Brush>, neprovede se žádná akce.  
  
 [!code-csharp[DragDropSnippets#DragEnter](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#dragenter)]
 [!code-vb[DragDropSnippets#DragEnter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#dragenter)]  
  
 <xref:System.Windows.DragDrop.DragOver> Nepřetržitě, zatímco data Přesune cíl přetažení, dojde k události. Tato událost se páruje s oblastí <xref:System.Windows.DragDrop.GiveFeedback> události ve zdroji přetažení. V <xref:System.Windows.DragDrop.DragOver> obslužná rutina události, obvykle se používá <xref:System.Windows.DataObject.GetDataPresent%2A> a <xref:System.Windows.DataObject.GetData%2A> metody, chcete-li zkontrolovat, zda přenášených dat ve formátu, která dokáže zpracovávat cíl přetažení. Můžete také zkontrolovat, zda jsou stisknutí jakékoli modifikační klávesy, která se obvykle signalizují, zda uživatel si klade za cíl akce přesunutí nebo kopírování. Po provedení těchto kontrol, nastavit <xref:System.Windows.DragEventArgs.Effects%2A?displayProperty=nameWithType> vlastnost oznámit přetahování zdroje, jaký vliv má vyřazení dat bude mít. Zdroje přetažení obdrží tyto informace <xref:System.Windows.DragDrop.GiveFeedback> argumenty události a nastavit odpovídající kurzor poskytněte zpětnou vazbu pro uživatele.  
  
 Následující příklad ukazuje <xref:System.Windows.DragDrop.DragOver> obslužné rutiny události pro <xref:System.Windows.Shapes.Ellipse> elementu. Tento kód zkontroluje, zda <xref:System.Windows.DataObject> přetažen nad třemi tečkami obsahuje data řetězce, který lze převést na <xref:System.Windows.Media.Brush>. Pokud ano, nastaví <xref:System.Windows.DragEventArgs.Effects%2A?displayProperty=nameWithType> vlastnost <xref:System.Windows.DragDropEffects.Copy>. Ke zdroji přetažení označuje, že data je možné zkopírovat do na tři tečky. Pokud data nelze převést na <xref:System.Windows.Media.Brush>, <xref:System.Windows.DragEventArgs.Effects%2A?displayProperty=nameWithType> je nastavena na <xref:System.Windows.DragDropEffects.None>. To znamená na zdroji přetažení, že se třemi tečkami není cíle přetažení platná data.  
  
 [!code-csharp[DragDropSnippets#DragOver](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#dragover)]
 [!code-vb[DragDropSnippets#DragOver](~/samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#dragover)]  
  
 <xref:System.Windows.DragDrop.DragLeave> Události dojde, když data ocitne mimo hranice cíle bez probíhá vyřazování. Zpracování této události cokoli, co jste to udělali v zpět <xref:System.Windows.DragDrop.DragEnter> obslužné rutiny události.  
  
 Následující příklad ukazuje <xref:System.Windows.DragDrop.DragLeave> obslužné rutiny události pro <xref:System.Windows.Shapes.Ellipse> elementu. Tento kód vrátí zpět provést ve verzi preview <xref:System.Windows.DragDrop.DragEnter> obslužné rutiny události s použitím uložené <xref:System.Windows.Media.Brush> na tři tečky.  
  
 [!code-csharp[DragDropSnippets#DragLeave](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#dragleave)]
 [!code-vb[DragDropSnippets#DragLeave](~/samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#dragleave)]  
  
 <xref:System.Windows.DragDrop.Drop> Při přetažení dat přes cíl přetažení, dojde k události; ve výchozím nastavení, to se stane, když se uvolní tlačítko myši. V <xref:System.Windows.DragDrop.Drop> obslužná rutina události, je použít <xref:System.Windows.DataObject.GetData%2A> metoda extrahovat přenášená data <xref:System.Windows.DataObject> a provádět žádné zpracovávání dat, který vaše aplikace vyžaduje. <xref:System.Windows.DragDrop.Drop> Událost skončí operace přetažení myší.  
  
 Následující příklad ukazuje <xref:System.Windows.DragDrop.Drop> obslužné rutiny události pro <xref:System.Windows.Shapes.Ellipse> elementu. Tento kód použije účinek operace přetažení myší a je podobný kód v <xref:System.Windows.DragDrop.DragEnter> obslužné rutiny události. Zkontroluje, jestli <xref:System.Windows.DataObject> přetažen nad třemi tečkami obsahuje data řetězce, který lze převést na <xref:System.Windows.Media.Brush>. Pokud ano, <xref:System.Windows.Media.Brush> se použije na tři tečky. Pokud data nelze převést na <xref:System.Windows.Media.Brush>, neprovede se žádná akce.  
  
 [!code-csharp[DragDropSnippets#Drop](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#drop)]
 [!code-vb[DragDropSnippets#Drop](~/samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#drop)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Clipboard>
- [Návod: Povolení přetahování na uživatelský ovládací prvek](walkthrough-enabling-drag-and-drop-on-a-user-control.md)
- [Témata s postupy](drag-and-drop-how-to-topics.md)
- [Přetažení](drag-and-drop.md)
