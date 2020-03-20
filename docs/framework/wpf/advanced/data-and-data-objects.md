---
title: Data a datové objekty
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data transfer [WPF], drag-and-drop
- DataFormats class [WPF]
- DataObject class [WPF]
ms.assetid: 5967d557-1867-420f-a524-ae3af78402da
ms.openlocfilehash: 532c254f997da183b073ddc9e00b4364ecfcd739
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186339"
---
# <a name="data-and-data-objects"></a>Data a datové objekty
Data, která jsou přenesena jako součást operace přetažení myší, jsou uložena v datovém objektu.  Koncepčně datový objekt se skládá z jednoho nebo více z následujících párů:  
  
- A <xref:System.Object> který obsahuje skutečná data.  
  
- Odpovídající identifikátor formátu dat.  
  
 Samotná data se mohou skládat z <xref:System.Object>čehokoliv, co může být reprezentováno jako základ .  Odpovídající formát dat je <xref:System.Type> řetězec nebo který poskytuje nápovědu o tom, v jakém formátu jsou data.  Datové objekty podporují hostování více dvojic datových/datových formátů; to umožňuje jeden datový objekt poskytovat data ve více formátech.  
  
<a name="Data_and_Data_Objects"></a>
## <a name="data-objects"></a>Datové objekty  
 Všechny datové objekty <xref:System.Windows.IDataObject> musí implementovat rozhraní, které poskytuje následující standardní sadu metod, které umožňují a usnadňují přenos dat.  
  
|Metoda|Souhrn|  
|------------|-------------|  
|<xref:System.Windows.IDataObject.GetData%2A>|Načte datový objekt v zadaném datovém formátu.|  
|<xref:System.Windows.IDataObject.GetDataPresent%2A>|Zkontroluje, zda jsou data k dispozici v zadaném formátu nebo zda je lze do ní převést.|  
|<xref:System.Windows.IDataObject.GetFormats%2A>|Vrátí seznam formátů, ve kterých jsou data v tomto datovém objektu uložena nebo na které lze převést.|  
|<xref:System.Windows.IDataObject.SetData%2A>|Ukládá zadaná data v tomto datovém objektu.|  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]poskytuje základní implementaci <xref:System.Windows.IDataObject> ve <xref:System.Windows.DataObject> třídě. Skladová <xref:System.Windows.DataObject> třída je dostatečná pro mnoho běžných scénářů přenosu dat.  
  
 Existuje několik předdefinovaných formátů, jako je bitmapa, CSV, soubor, HTML, RTF, řetězec, text a zvuk. Informace o předdefinovaných formátech dat [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]dodaných <xref:System.Windows.DataFormats> s , naleznete v tématu odkazu na třídu.  
  
 Datové objekty běžně zahrnují zařízení pro automatický převod dat uložených v jednom formátu do jiného formátu při extrahování dat; Toto zařízení se označuje jako automatický převod. Při dotazování na datové formáty dostupné v datovém objektu lze automaticky konvertibilní <xref:System.Windows.DataObject.GetFormats%28System.Boolean%29> <xref:System.Windows.DataObject.GetDataPresent%28System.String%2CSystem.Boolean%29> datové formáty `autoConvert` filtrovat `false`z nativních datových formátů voláním metody nebo a zadáním parametru jako .  Při přidávání dat do <xref:System.Windows.DataObject.SetData%28System.String%2CSystem.Object%2CSystem.Boolean%29> datového objektu pomocí metody lze automatický `autoConvert` převod `false`dat zakázat nastavením parametru na .  
  
<a name="Working_with_Data_Objects"></a>
## <a name="working-with-data-objects"></a>Práce s datovými objekty  
 Tato část popisuje běžné techniky pro vytváření a práci s datovými objekty.  
  
### <a name="creating-new-data-objects"></a>Vytváření nových datových objektů  
 Třída <xref:System.Windows.DataObject> poskytuje několik přetížených konstruktorů, které usnadňují <xref:System.Windows.DataObject> naplnění nové instance s jedním párem datového formátu.  
  
 Následující ukázkový kód vytvoří nový datový objekt a použije <xref:System.Windows.DataObject.%23ctor%2A>jeden<xref:System.Windows.DataObject.%23ctor(System.String,System.Object)>z přetížených konstruktorů ( ) k inicializaci datového objektu pomocí řetězce a zadaného datového formátu.  V tomto případě je formát dat určen řetězcem; <xref:System.Windows.DataFormats> třída poskytuje sadu předdefinovaných řetězců typů. Automatický převod uložených dat je ve výchozím nastavení povolen.  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_typestring)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_typestring)]  
  
 Další příklady kódu, který vytváří datový objekt, naleznete [v tématu Vytvoření datového objektu](how-to-create-a-data-object.md).  
  
### <a name="storing-data-in-multiple-formats"></a>Ukládání dat ve více formátech  
 Jeden datový objekt je schopen ukládat data ve více formátech.   Strategické použití více datových formátů v rámci jednoho datového objektu potenciálně umožňuje datový objekt spotřební širší škálu cílů přetažení, než kdyby mohl být reprezentován pouze jeden datový formát.  Všimněte si, že obecně zdroj přetažení musí být agnostik o formáty dat, které jsou spotřební podle potenciální cíle přetažení.  
  
 Následující příklad ukazuje, jak <xref:System.Windows.DataObject.SetData%28System.String%2CSystem.Object%29> pomocí metody přidat data do datového objektu ve více formátech.  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_StoreMultipleFormats](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_storemultipleformats)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_StoreMultipleFormats](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_storemultipleformats)]  
  
### <a name="querying-a-data-object-for-available-formats"></a>Dotazování na datový objekt pro dostupné formáty  
 Vzhledem k tomu, že jeden datový objekt může obsahovat libovolný počet datových formátů, zahrnují datové objekty zařízení pro načítání seznamu dostupných datových formátů.  
  
 Následující ukázkový kód <xref:System.Windows.DataObject.GetFormats%2A> používá přetížení k získání pole řetězců označujících všechny datové formáty dostupné v datovém objektu (nativní i automaticky převést).  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getalldataformats)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getalldataformats)]  
  
 Další příklady kódu, který se dotazuje datového objektu na dostupné formáty dat, naleznete [v tématu Seznam datových formátů v datovém objektu](how-to-list-the-data-formats-in-a-data-object.md).  Příklady dotazování datového objektu na přítomnost určitého datového formátu naleznete v tématu [Určení, zda je datový formát přítomen v datovém objektu](how-to-determine-if-a-data-format-is-present-in-a-data-object.md).  
  
### <a name="retrieving-data-from-a-data-object"></a>Načítání dat z datového objektu  
 Načítání dat z datového objektu v určitém formátu <xref:System.Windows.DataObject.GetData%2A> jednoduše zahrnuje volání jedné z metod a určení požadovaného formátu dat.  Jednou z <xref:System.Windows.DataObject.GetDataPresent%2A> metod lze zkontrolovat přítomnost určitého datového formátu.  <xref:System.Windows.DataObject.GetData%2A>vrátí data v <xref:System.Object>; v závislosti na formátu dat může být tento objekt přetypován do kontejneru specifického pro daný typ.  
  
 Následující ukázkový kód <xref:System.Windows.DataObject.GetDataPresent%28System.String%29> používá přetížení ke kontrole, zda je k dispozici zadaný formát dat (nativní nebo automatickým převodem). Pokud je k dispozici zadaný formát, příklad <xref:System.Windows.DataObject.GetData%28System.String%29> načte data pomocí metody.  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getspecificdataformat)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getspecificdataformat)]  
  
 Další příklady kódu, který načítá data z datového objektu, naleznete [v tématu Načtení dat v konkrétním datovém formátu](how-to-retrieve-data-in-a-particular-data-format.md).  
  
### <a name="removing-data-from-a-data-object"></a>Odebrání dat z datového objektu  
 Data nelze přímo odebrat z datového objektu.  Chcete-li efektivně odebrat data z datového objektu, postupujte takto:  
  
1. Vytvořte nový datový objekt, který bude obsahovat pouze data, která chcete zachovat.  
  
2. "Zkopírujte" požadovaná data ze starého datového objektu do nového datového objektu.  Chcete-li data zkopírovat, <xref:System.Windows.DataObject.GetData%2A> použijte jednu z metod k načtení <xref:System.Object> nezpracovaná data, která obsahuje nezpracovaná data, a pak použijte jednu <xref:System.Windows.DataObject.SetData%2A> z metod k přidání dat do nového datového objektu.  
  
3. Nahraďte starý datový objekt novým.  
  
> [!NOTE]
> Metody <xref:System.Windows.DataObject.SetData%2A> pouze přidat data do datového objektu; nenahrazují data, a to ani v případě, že data a formát dat jsou přesně stejné jako předchozí volání. Volání <xref:System.Windows.DataObject.SetData%2A> dvakrát pro stejný formát dat a dat bude mít za následek data /datový formát je přítomen dvakrát v datovém objektu.
