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
ms.openlocfilehash: 06c74548ebe9d01a15cea72f409eaa6df9c8d6de
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="drag-and-drop-overview"></a>Přehled přetažení
Toto téma obsahuje přehled podpory přetažení myší v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikace. Přetažení myší běžně odkazuje na metodu přenosu dat, který zahrnuje pomocí myši (nebo jiné polohovací zařízení) a vyberte jeden nebo více objektů, přetáhněte tyto objekty přes cíle některé požadované přetažení v [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]a jejich vyřazení.  
  
  
<a name="Drag_and_Drop_Support"></a>   
## <a name="drag-and-drop-support-in-wpf"></a>Podpora přetažení myší v grafickém subsystému WPF  
 Operací přetažení myší obvykle zahrnuje dvě strany: přetažení zdroj, ze které pochází objekt taženou a cíle přetažení, která přijímá objekt vynechaných.  Přetáhněte zdroje a drop cíl může být prvky uživatelského rozhraní na stejnou aplikaci nebo v jiné aplikaci.  
  
 Je zcela libovolný typ a počet objektů, které smí uživatel manipulovat s přetažení myší. Například soubory, složky a výběr obsahu jsou některé z běžnějších objektů s nimi manipulovat, prostřednictvím operací přetažení myší.  
  
 Konkrétní akce prováděné během operace přetažení myší jsou aplikace konkrétní a často určenému kontextu.  Například přetažení výběru souborů z jedné složky do jiné na stejném zařízení úložiště přesune soubory ve výchozím nastavení, že přetáhnete soubory z [!INCLUDE[TLA#tla_unc](../../../../includes/tlasharptla-unc-md.md)] sdílenou složku do místní složky zkopíruje soubory ve výchozím nastavení.  
  
 Přetažení myší poskytované systémem [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jsou navržené jako vysoce flexibilní a přizpůsobitelné podporuje celou řadu scénářů přetažení myší.  Přetažení myší podporuje práci s objekty v rámci jedné aplikace, nebo mezi různými aplikacemi. Přetahování a uvolnění mezi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] také plně podporuje aplikace a další aplikace systému Windows.  
  
 V [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], jakékoliv <xref:System.Windows.UIElement> nebo <xref:System.Windows.ContentElement> mohl účastnit přetažení myší. Události a metody potřebné pro operací přetažení myší jsou definovány v <xref:System.Windows.DragDrop> třídy. <xref:System.Windows.UIElement> a <xref:System.Windows.ContentElement> třídy obsahovat aliasy pro <xref:System.Windows.DragDrop> přidružené události tak, aby události se zobrazí ve třídě seznam členů, kdy <xref:System.Windows.UIElement> nebo <xref:System.Windows.ContentElement> zdědí jako základní prvek. Obslužné rutiny událostí, které jsou připojené k tyto události jsou připojené k základní <xref:System.Windows.DragDrop> přidružená událost a přijímat stejné instance dat události. Další informace najdete v tématu <xref:System.Windows.UIElement.Drop?displayProperty=nameWithType> událostí.  
  
> [!IMPORTANT]
>  OLE a přetažení nefunguje v zóně Internet.  
  
<a name="Data_Transfer"></a>   
## <a name="data-transfer"></a>Přenos dat  
 Přetažení myší je součástí oblasti obecnější přenosu dat. Přenos dat zahrnuje operace přetahování myší a kopírování a vkládání. Operaci přetažení myší je podobná operace kopírování a vkládání nebo vyjímání a vkládání, který se používá k přenosu dat z jednoho objektu nebo aplikací na jiný pomocí schránky systému. Oba typy operací vyžadují:  
  
-   Zdrojový objekt, který poskytuje data.  
  
-   Způsob, jak dočasně uložit přenášená data.  
  
-   Cílový objekt, který přijímá data.  
  
 V operaci kopírování a vkládání do schránky systému se používá k dočasnému uložení přenášených dat; v operaci přetažení myší <xref:System.Windows.DataObject> se používá k ukládání dat. Koncepčně, obsahuje jeden nebo více páry datový objekt <xref:System.Object> skutečná data a odpovídající identifikátor formát dat, který obsahuje.  
  
 Zdroje operace přetažení zahájí operaci přetažení myší pomocí volání statických <xref:System.Windows.DragDrop.DoDragDrop%2A?displayProperty=nameWithType> metoda a předání přenášených dat do ní. <xref:System.Windows.DragDrop.DoDragDrop%2A> Metoda budou automaticky zahrnovat data v <xref:System.Windows.DataObject> v případě potřeby. Pro větší kontrolu nad formát dat, může obtékat data v <xref:System.Windows.DataObject> před předáním na <xref:System.Windows.DragDrop.DoDragDrop%2A> metoda. Cíle přetažení zodpovídá za extrahování dat z <xref:System.Windows.DataObject>. Další informace o práci s objekty dat najdete v tématu [datových objektů a dat](../../../../docs/framework/wpf/advanced/data-and-data-objects.md).  
  
 Zdrojové a cílové operací přetažení myší jsou prvky uživatelského rozhraní; data, která je ve skutečnosti přenášení obvykle nemá vizuální reprezentace. Můžete napsat kód zajistit vizuální znázornění dat, která je přetáhnout, jako například nastane, když přetahování souborů v Průzkumníku Windows. Ve výchozím nastavení poskytnutí zpětné vazby pro uživatele tak, že změníte kurzor představují o tom, že bude mít operaci přetažení myší na data, například zda budou data přesunout ani zkopírovat.  
  
### <a name="drag-and-drop-effects"></a>Účinky přetažení myší  
 Jiný vliv na přenášených dat může mít operací přetažení myší. Například můžete zkopírovat data nebo můžete přesunout data. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] definuje <xref:System.Windows.DragDropEffects> výčet, který můžete použít k určení vliv operací přetažení myší. V zdroje operace přetažení, můžete zadat účinky, které vám umožní zdroji v <xref:System.Windows.DragDrop.DoDragDrop%2A> metoda. V cíle přetažení, můžete zadat o tom, že cíl chce <xref:System.Windows.DragEventArgs.Effects%2A> vlastnost <xref:System.Windows.DragEventArgs> třídy. Když cíle přetažení určuje jeho dopad určený v <xref:System.Windows.DragDrop.DragOver> událostí, které se předávají informace zpět do zdroje operace přetažení ve <xref:System.Windows.DragDrop.GiveFeedback> událostí. Zdroje operace přetažení používá tuto informaci k informovat uživatele o tom, jaký vliv má cíle přetažení chtít mít na data. Při umístění dat cíle přetažení určuje skutečné účinek <xref:System.Windows.DragDrop.Drop> událostí. Aby se předávají informace zpět do zdroje operace přetažení jako návratová hodnota <xref:System.Windows.DragDrop.DoDragDrop%2A> metoda. Pokud cíle přetažení vrátí efektu, který není v seznamu zdroje přetažení `allowedEffects`, přetažení myší operace byla zrušena, bez jakékoli přenos dat, ke kterým dochází.  
  
 Je důležité si pamatovat, že v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], <xref:System.Windows.DragDropEffects> hodnoty se používají jenom pro komunikaci mezi zdroje operace přetažení a cíle přetažení o důsledcích operaci přetažení myší. Skutečný výsledek operace přetažení myší závisí na vás bude psaní příslušný kód ve vaší aplikaci.  
  
 Cíle přetažení například mohla uvádět, že účinek vyřazení dat na něm je přesouvat data. Ale pokud chcete přesunout data, musí být jak přidat do cílového elementu a odebrat z source element. Source element může znamenat, že umožňuje přesun dat, ale pokud nezadáte kód, který odeberte data ze zdrojového prvku, konečný výsledek bude, že data jsou zkopírovány a není přesunut.  
  
<a name="Drag_and_Drop_Events"></a>   
## <a name="drag-and-drop-events"></a>Události a přetažení  
 Operací přetažení myší podporovat model řízených událostmi.  Zdroje operace přetažení a cíle přetažení použijte standardní sadu událostí, které pro zpracování operací přetažení myší.  Následující tabulka představuje souhrn standardní události přetažení myší. Tyto jsou přidružené události na <xref:System.Windows.DragDrop> třídy. Další informace o přidružené události najdete v tématu [připojen přehled událostí](../../../../docs/framework/wpf/advanced/attached-events-overview.md).  
  
### <a name="drag-source-events"></a>Události zdroje přetažení  
  
|Událost|Souhrn|  
|-----------|-------------|  
|<xref:System.Windows.DragDrop.GiveFeedback>|Tato událost nastane nepřetržitě během operace přetahování myší a umožňuje zdroj vynechání poskytnout zpětnou vazbu informací uživateli. Tato běžně zpětné změnou vzhled ukazatele myši k označení důsledky povolenou cíle přetažení.  Toto je probublávání událost.|  
|<xref:System.Windows.DragDrop.QueryContinueDrag>|K této události dojde, když dojde ke změně v klávesnici nebo tlačítko myši stavy během operace přetahování myší a umožňuje zdroj vynechání ke zrušení operace přetažení myší v závislosti na klíč nebo tlačítko stavy. Toto je probublávání událost.|  
|<xref:System.Windows.DragDrop.PreviewGiveFeedback>|Tunelové verzi <xref:System.Windows.DragDrop.GiveFeedback>.|  
|<xref:System.Windows.DragDrop.PreviewQueryContinueDrag>|Tunelové verzi <xref:System.Windows.DragDrop.QueryContinueDrag>.|  
  
### <a name="drop-target-events"></a>Cíl události  
  
|Událost|Souhrn|  
|-----------|-------------|  
|<xref:System.Windows.DragDrop.DragEnter>|K této události dojde, když je objekt přetažen cíle přetažení hranic. Toto je probublávání událost.|  
|<xref:System.Windows.DragDrop.DragLeave>|K této události dojde, když objekt ocitne mimo hranice cíle přetažení.  Toto je probublávání událost.|  
|<xref:System.Windows.DragDrop.DragOver>|Průběžně, pokud je objekt přetáhnout (přesunutý) v rámci hranice cíle přetažení dojde k této události. Toto je probublávání událost.|  
|<xref:System.Windows.DragDrop.Drop>|K této události dojde, když objektu je vyřazeno na cíle přetažení.  Toto je probublávání událost.|  
|<xref:System.Windows.DragDrop.PreviewDragEnter>|Tunelové verzi <xref:System.Windows.DragDrop.DragEnter>.|  
|<xref:System.Windows.DragDrop.PreviewDragLeave>|Tunelové verzi <xref:System.Windows.DragDrop.DragLeave>.|  
|<xref:System.Windows.DragDrop.PreviewDragOver>|Tunelové verzi <xref:System.Windows.DragDrop.DragOver>.|  
|<xref:System.Windows.DragDrop.PreviewDrop>|Tunelové verzi <xref:System.Windows.DragDrop.Drop>.|  
  
 Zpracování událostí a přetažení pro instance objektu, přidejte obslužné rutiny pro události uvedené v předchozích tabulkách. Zpracování událostí přetažení myší na úrovni třídy, přepsání odpovídající virtuální na * události a na\*PreviewEvent metody. Další informace najdete v tématu [– třída zpracování o směrované události podle základní třídy ovládacích prvků](../../../../docs/framework/wpf/advanced/marking-routed-events-as-handled-and-class-handling.md#Class_Handling_of_Routed_Events).  
  
<a name="Implementing_Drag_And_Drop"></a>   
## <a name="implementing-drag-and-drop"></a>Implementace a přetažení  
 Element uživatelského rozhraní lze zdroje operace přetažení, cíle přetažení nebo obojí. K implementaci základní přetahování myší, můžete napsat kód pro zahájení operace přetahování myší a zpracování vynechaných data. Přetažení myší prostředí můžete vylepšit zpracování události volitelné přetažení myší.  
  
 K implementaci základní přetahování myší, dokončí následující úkoly:  
  
-   Identifikujte elementu, který bude zdroje operace přetažení. Může být zdroje operace přetažení <xref:System.Windows.UIElement> nebo <xref:System.Windows.ContentElement>.  
  
-   Vytvořte obslužnou rutinu události na zdroje operace přetažení, která zahájí operaci přetažení myší. Událost je obvykle <xref:System.Windows.UIElement.MouseMove> událostí.  
  
-   V obslužné rutině události zdroje přetažení volání <xref:System.Windows.DragDrop.DoDragDrop%2A> metoda inicializace operace přetažení myší. V <xref:System.Windows.DragDrop.DoDragDrop%2A> volat funkci, zadejte zdroje operace přetažení, přenos dat a povolených důsledky.  
  
-   Identifikujte elementu, který bude cíle přetažení. Může být cíle přetažení <xref:System.Windows.UIElement> nebo <xref:System.Windows.ContentElement>.  
  
-   Na cíle přetažení nastavená <xref:System.Windows.UIElement.AllowDrop%2A> vlastnost `true`.  
  
-   V cíle přetažení, vytvořte <xref:System.Windows.DragDrop.Drop> obslužné rutiny události ke zpracování vynechaných data.  
  
-   V <xref:System.Windows.DragDrop.Drop> obslužné rutiny události, extrahovat data z <xref:System.Windows.DragEventArgs> pomocí <xref:System.Windows.DataObject.GetDataPresent%2A> a <xref:System.Windows.DataObject.GetData%2A> metody.  
  
-   V <xref:System.Windows.DragDrop.Drop> obslužné rutiny události, data použít k provedení požadované operace přetažení myší.  
  
 Implementace přetažení myší můžete vylepšit tak, že vytvoříte vlastní <xref:System.Windows.DataObject> a ve zpracování volitelné přetáhněte zdroje a drop cíl události, jak je znázorněno v následující úlohy:  
  
-   Pro přenos vlastních dat nebo více datových položek, vytvořit <xref:System.Windows.DataObject> mají být předány <xref:System.Windows.DragDrop.DoDragDrop%2A> metoda.  
  
-   K provedení dalších akcí během přetažení, zpracování <xref:System.Windows.DragDrop.DragEnter>, <xref:System.Windows.DragDrop.DragOver>, a <xref:System.Windows.DragDrop.DragLeave> události na cíle přetažení.  
  
-   Chcete-li změnit vzhled ukazatele myši, zpracování <xref:System.Windows.DragDrop.GiveFeedback> událostí na zdroje operace přetažení.  
  
-   Pokud chcete změnit, jak zrušit operaci přetažení myší, zpracování <xref:System.Windows.DragDrop.QueryContinueDrag> událostí na zdroje operace přetažení.  
  
<a name="Drag_And_Drop_Example"></a>   
## <a name="drag-and-drop-example"></a>Příklad přetažení myší  
 Tato část popisuje, jak implementovat přetažení myší pro <xref:System.Windows.Shapes.Ellipse> elementu. <xref:System.Windows.Shapes.Ellipse> Zdroje operace přetažení a cíle přetažení. Přenášených dat je řetězcová reprezentace se třemi tečkami <xref:System.Windows.Shapes.Shape.Fill%2A> vlastnost. Následující XAML ukazuje <xref:System.Windows.Shapes.Ellipse> elementu a přetažení myší související události, které zpracovává. Úplné kroky pro implementaci přetahování myší, najdete v části [návod: povolení přetáhněte a Drop na uživatelský ovládací prvek](../../../../docs/framework/wpf/advanced/walkthrough-enabling-drag-and-drop-on-a-user-control.md).  
  
 [!code-xaml[DragDropSnippets#EllipseXaml](../../../../samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml#ellipsexaml)]  
  
### <a name="enabling-an-element-to-be-a-drag-source"></a>Povolení elementu jako zdroje operace přetažení  
 Objekt, který je zdroje operace přetažení zodpovídá za:  
  
-   Identifikace, když dojde přetažení.  
  
-   Probíhá inicializace operaci přetažení myší.  
  
-   Určení dat, které se mají přenést.  
  
-   Zadání účinky, které mají na přenášených dat je povoleno operaci přetažení myší.  
  
 Zdroje operace přetažení může také váš názor uživateli ohledně povolených akcí (přesunout, kopírovat, none) a můžete zrušit operaci přetažení myší na další uživatelský vstup, jako je například stisknutí klávesy ESC při tažení základě.  
  
 Je zodpovědností aplikace k určení, kdy dojde k přetáhněte, a poté operaci spustit přetažení myší pomocí volání <xref:System.Windows.DragDrop.DoDragDrop%2A> metoda. Obvykle se jedná, kdy <xref:System.Windows.UIElement.MouseMove> přes element přetáhnout při stisknutí tlačítka myši dojde k události. Následující příklad ukazuje, jak zahájit operaci přetažení myší z <xref:System.Windows.UIElement.MouseMove> obslužnou rutinu události <xref:System.Windows.Shapes.Ellipse> element aby zdroje operace přetažení. Přenášených dat je řetězcová reprezentace se třemi tečkami <xref:System.Windows.Shapes.Shape.Fill%2A> vlastnost.  
  
 [!code-csharp[DragDropSnippets#DoDragDrop](../../../../samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#dodragdrop)]
 [!code-vb[DragDropSnippets#DoDragDrop](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#dodragdrop)]  
  
 Uvnitř <xref:System.Windows.UIElement.MouseMove> obslužné rutiny události, volání <xref:System.Windows.DragDrop.DoDragDrop%2A> metoda inicializace operace přetažení myší. <xref:System.Windows.DragDrop.DoDragDrop%2A> Metoda přijímá tři parametry:  
  
-   `dragSource` – Odkaz na objekt závislostí, který je zdrojem přenášených dat; Toto je obvykle zdroj <xref:System.Windows.UIElement.MouseMove> událostí.  
  
-   `data` -Objekt, který obsahuje přenášených dat, uzavřen do <xref:System.Windows.DataObject>.  
  
-   `allowedEffects` -Jedním z <xref:System.Windows.DragDropEffects> hodnot výčtu, která určuje povolené důsledky operaci přetažení myší.  
  
 Jakýkoli serializovatelný objekt lze předat ve `data` parametr. Pokud data není již uzavřen do <xref:System.Windows.DataObject>, bude automaticky zalomit v nové <xref:System.Windows.DataObject>. Pokud chcete předat více datových položek, musíte vytvořit <xref:System.Windows.DataObject> sami, možností a předejte ji do <xref:System.Windows.DragDrop.DoDragDrop%2A> metoda. Další informace najdete v tématu [datových objektů a dat](../../../../docs/framework/wpf/advanced/data-and-data-objects.md).  
  
 `allowedEffects` Parametr se používá k určení, co bude zdroje operace přetažení povolit cíle přetažení dělat s přenášená data. Běžné hodnoty pro zdroje operace přetažení jsou <xref:System.Windows.DragDropEffects.Copy>, <xref:System.Windows.DragDropEffects.Move>, a <xref:System.Windows.DragDropEffects.All>.  
  
> [!NOTE]
>  Cíle přetažení je také možné zadat jaké důsledky hodlá v reakci na vynechaných data. Například pokud cíle přetažení nebyl rozpoznán typ dat chcete vyřadit, ho můžete odmítnout data nastavením jeho povolené účinky na <xref:System.Windows.DragDropEffects.None>. Obvykle dělá to jeho <xref:System.Windows.DragDrop.DragOver> obslužné rutiny události.  
  
 Volitelně může zpracovat zdroje operace přetažení <xref:System.Windows.DragDrop.GiveFeedback> a <xref:System.Windows.DragDrop.QueryContinueDrag> události. Tyto události mít výchozí obslužné rutiny, které se používají, pokud označíte události jako zpracování. Tyto události bude obvykle ignorovat, pokud máte konkrétní potřebu změnit jejich výchozí chování.  
  
 <xref:System.Windows.DragDrop.GiveFeedback> Událost se vyvolá nepřetržitě při přetažení zdroje operace přetažení. Výchozí obslužnou rutinu pro tuto událost, zkontroluje, jestli zdroje operace přetažení přes cíle přetažení platný. Pokud se jedná, zkontroluje povolený důsledky cíle přetažení. Poté přiřadí zpětnou vazbu pro koncového uživatele o důsledky povolené rozevírací. To se obvykle provádí změna myší na Ne pokles, kopírování nebo přesunutí kurzoru. Tato událost by měla řídit jenom v případě budete muset použít vlastní kurzory k poskytnutí zpětné vazby pro uživatele. Pokud tuto událost zpracovat, je nutné označit ji jako zpracování tak, aby obslužná rutina výchozí nepřepisuje vaší obslužné rutiny.  
  
 <xref:System.Windows.DragDrop.QueryContinueDrag> Událost se vyvolá nepřetržitě při přetažení zdroje operace přetažení. Dokáže zpracovat tuto událost, chcete-li určit, jakou akci ukončí operaci přetažení myší podle stavu ESC, SHIFT, CTRL a ALT – klávesy, jakož i stav tlačítka myši. Operaci přetažení myší výchozí obslužnou rutinu pro tuto událost zruší, pokud stisknutí klávesy ESC a zahodí data, pokud uvolnění tlačítka myši.  
  
> [!CAUTION]
>  Tyto události jsou vyvolány nepřetržitě během operace přetažení myší. Proto byste neměli náročných úloh v obslužné rutiny událostí.  Například v mezipaměti kurzoru použít místo vytvoření nové kurzoru pokaždé, když <xref:System.Windows.DragDrop.GiveFeedback> událost se vyvolá.  
  
### <a name="enabling-an-element-to-be-a-drop-target"></a>Povolení elementu jako cíl vyřadit  
 Objekt, který je cíle přetažení zodpovídá za:  
  
-   Určení, že se jedná o cíle přetažení platný.  
  
-   Odpovídá na požadavky zdroje operace přetažení, když se nastavuje tažením přes cíl.  
  
-   Kontroluje, že přenášených dat je ve formátu, který může přijímat.  
  
-   Zpracování vynechaných data.  
  
 Chcete-li určit, že je element cíle přetažení, nastavíte jeho <xref:System.Windows.UIElement.AllowDrop%2A> vlastnost `true`. Cíl události rozevírací pak bude vydána v elementu tak, aby bylo možné zpracovat, je. Během operace přetahování myší dojde k následujícímu pořadí událostí na cíle přetažení:  
  
1.  <xref:System.Windows.DragDrop.DragEnter>  
  
2.  <xref:System.Windows.DragDrop.DragOver>  
  
3.  <xref:System.Windows.DragDrop.DragLeave> Nebo <xref:System.Windows.DragDrop.Drop>  
  
 <xref:System.Windows.DragDrop.DragEnter> Události dojde, když data je přetáhnout do cíle přetažení hranic. Tuto událost zajistit náhled důsledky operace přetahování myší, je obvykle zpracovat, pokud je to vhodné pro vaši aplikaci. Nenastavujte <xref:System.Windows.DragEventArgs.Effects%2A?displayProperty=nameWithType> vlastnost <xref:System.Windows.DragDrop.DragEnter> událostí, jak se budou přepsány v <xref:System.Windows.DragDrop.DragOver> událostí.  
  
 Následující příklad ukazuje <xref:System.Windows.DragDrop.DragEnter> obslužné rutiny události pro <xref:System.Windows.Shapes.Ellipse> elementu. Tento kód zobrazí důsledky operaci přetažení myší náhled uložením aktuální <xref:System.Windows.Shapes.Shape.Fill%2A> štětce. Poté použije <xref:System.Windows.DataObject.GetDataPresent%2A> metoda zkontrolujte zda <xref:System.Windows.DataObject> přes se třemi tečkami přetažen obsahuje řetězec data, která lze převést na <xref:System.Windows.Media.Brush>. Pokud ano, data jsou extrahována pomocí <xref:System.Windows.DataObject.GetData%2A> metoda. Pak je převést na <xref:System.Windows.Media.Brush> a použity na se třemi tečkami. Změna je vrácen v <xref:System.Windows.DragDrop.DragLeave> obslužné rutiny události. Pokud data nelze převést na <xref:System.Windows.Media.Brush>, neprovede se žádná akce.  
  
 [!code-csharp[DragDropSnippets#DragEnter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#dragenter)]
 [!code-vb[DragDropSnippets#DragEnter](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#dragenter)]  
  
 <xref:System.Windows.DragDrop.DragOver> Nepřetržitě při přetažení data přes cíle přetažení dojde k události. Tato událost je spárován s <xref:System.Windows.DragDrop.GiveFeedback> událostí na zdroje operace přetažení. V <xref:System.Windows.DragDrop.DragOver> obslužné rutiny události, obvykle použijete <xref:System.Windows.DataObject.GetDataPresent%2A> a <xref:System.Windows.DataObject.GetData%2A> metody a zkontrolujte, zda přenášených dat ve formátu, který může zpracovat cíle přetažení. Můžete také zkontrolovat, zda všechny modifikátor stisknutí kláves, což obvykle označí, zda uživatel má v úmyslu akce přesunutí nebo kopírování. Po těchto ověřování, je třeba nastavit <xref:System.Windows.DragEventArgs.Effects%2A?displayProperty=nameWithType> vlastnost oznámit přetahování zdroje, jaký vliv má vyřazení dat bude mít. Zdroje operace přetažení obdrží tyto informace <xref:System.Windows.DragDrop.GiveFeedback> argumentů události a můžete nastavit v příslušné kurzor poskytněte zpětnou vazbu pro uživatele.  
  
 Následující příklad ukazuje <xref:System.Windows.DragDrop.DragOver> obslužné rutiny události pro <xref:System.Windows.Shapes.Ellipse> elementu. Tento kód zkontroluje, zda <xref:System.Windows.DataObject> přes se třemi tečkami přetažen obsahuje řetězec data, která lze převést na <xref:System.Windows.Media.Brush>. Pokud ano, nastaví <xref:System.Windows.DragEventArgs.Effects%2A?displayProperty=nameWithType> vlastnost <xref:System.Windows.DragDropEffects.Copy>. To znamená na zdroje operace přetažení, že data je možné zkopírovat do se třemi tečkami. Pokud data nelze převést na <xref:System.Windows.Media.Brush>, <xref:System.Windows.DragEventArgs.Effects%2A?displayProperty=nameWithType> je nastavena na <xref:System.Windows.DragDropEffects.None>. To znamená na zdroje operace přetažení se třemi tečkami není cíle přetažení platná data.  
  
 [!code-csharp[DragDropSnippets#DragOver](../../../../samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#dragover)]
 [!code-vb[DragDropSnippets#DragOver](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#dragover)]  
  
 <xref:System.Windows.DragDrop.DragLeave> Události dojde, když data bez vyřazována ocitne mimo hranice cílové složky. Zpracování této události všechno, co jste to udělali v vrátit zpět <xref:System.Windows.DragDrop.DragEnter> obslužné rutiny události.  
  
 Následující příklad ukazuje <xref:System.Windows.DragDrop.DragLeave> obslužné rutiny události pro <xref:System.Windows.Shapes.Ellipse> elementu. Tento kód vrátí zpět ve verzi preview prováděla <xref:System.Windows.DragDrop.DragEnter> obslužné rutiny události použitím uložené <xref:System.Windows.Media.Brush> k se třemi tečkami.  
  
 [!code-csharp[DragDropSnippets#DragLeave](../../../../samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#dragleave)]
 [!code-vb[DragDropSnippets#DragLeave](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#dragleave)]  
  
 <xref:System.Windows.DragDrop.Drop> Události dojde, když je vyřazeno data přes cíle přetažení; ve výchozím nastavení, to se stane, když uvolnění tlačítka myši. V <xref:System.Windows.DragDrop.Drop> obslužné rutiny události, můžete použít <xref:System.Windows.DataObject.GetData%2A> metoda extrahování přenášených dat z <xref:System.Windows.DataObject> a provádět všechny zpracování dat, která vaše aplikace vyžaduje. <xref:System.Windows.DragDrop.Drop> Událostí ukončí operaci přetažení myší.  
  
 Následující příklad ukazuje <xref:System.Windows.DragDrop.Drop> obslužné rutiny události pro <xref:System.Windows.Shapes.Ellipse> elementu. Tento kód používá důsledky operaci přetažení myší a je podobný kódu v <xref:System.Windows.DragDrop.DragEnter> obslužné rutiny události. Kontroluje, zda <xref:System.Windows.DataObject> přes se třemi tečkami přetažen obsahuje řetězec data, která lze převést na <xref:System.Windows.Media.Brush>. Pokud ano, <xref:System.Windows.Media.Brush> se použije pro se třemi tečkami. Pokud data nelze převést na <xref:System.Windows.Media.Brush>, neprovede se žádná akce.  
  
 [!code-csharp[DragDropSnippets#Drop](../../../../samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#drop)]
 [!code-vb[DragDropSnippets#Drop](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#drop)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Clipboard>  
 [Návod: Povolení přetahování pomocí myši na uživatelském ovládacím prvku](../../../../docs/framework/wpf/advanced/walkthrough-enabling-drag-and-drop-on-a-user-control.md)  
 [Témata s postupy](../../../../docs/framework/wpf/advanced/drag-and-drop-how-to-topics.md)  
 [Přetažení](../../../../docs/framework/wpf/advanced/drag-and-drop.md)
