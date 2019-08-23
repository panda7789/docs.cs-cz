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
ms.openlocfilehash: 4b948a64a14df7ea79b54b810f734056d57ef406
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964855"
---
# <a name="data-and-data-objects"></a>Data a datové objekty
Data, která se přenášejí jako součást operace přetažení, se ukládají do datového objektu.  V koncepčním případě se datový objekt skládá z jednoho nebo více následujících párů:  
  
- <xref:System.Object> Obsahující skutečná data.  
  
- Odpovídající identifikátor formátu dat.  
  
 Samotná data mohou být tvořena cokoli, co může být reprezentována jako základní <xref:System.Object>.  Odpovídající formát dat je řetězec nebo <xref:System.Type> , který poskytuje nápovědu k formátování dat.  Datové objekty podporují hostování více párů datových nebo datových formátů. To umožňuje, aby jeden datový objekt poskytoval data v několika formátech.  
  
<a name="Data_and_Data_Objects"></a>   
## <a name="data-objects"></a>Datové objekty  
 Všechny datové objekty musí implementovat <xref:System.Windows.IDataObject> rozhraní, které poskytuje následující standardní sadu metod, které umožňují a usnadňují přenos dat.  
  
|Metoda|Souhrn|  
|------------|-------------|  
|<xref:System.Windows.IDataObject.GetData%2A>|Načte datový objekt v zadaném datovém formátu.|  
|<xref:System.Windows.IDataObject.GetDataPresent%2A>|Zkontroluje, zda jsou data v nástroji k dispozici, nebo je lze převést na určený formát.|  
|<xref:System.Windows.IDataObject.GetFormats%2A>|Vrátí seznam formátů, v nichž jsou data v tomto datovém objektu uložena, nebo je lze převést na.|  
|<xref:System.Windows.IDataObject.SetData%2A>|Ukládá zadaná data do tohoto datového objektu.|  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]poskytuje základní implementaci <xref:System.Windows.IDataObject> <xref:System.Windows.DataObject> ve třídě. Třída akcie <xref:System.Windows.DataObject> je dostačující pro mnoho běžných scénářů přenosu dat.  
  
 K dispozici je několik předem definovaných formátů, jako jsou rastrové obrázky, CSV, soubor, HTML, RTF, text a zvuk. Informace o předem definovaných formátech dat, které jsou k [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]dispozici v <xref:System.Windows.DataFormats> nástroji, naleznete v tématu věnovaném odkazům na třídu.  
  
 Datové objekty běžně zahrnují zařízení pro automatické převedení dat uložených v jednom formátu do jiného formátu při extrakci dat. Toto zařízení se označuje jako automaticky převedené. Při dotazování na formáty dat, které jsou k dispozici v datovém objektu, lze automaticky převoditelné formáty dat filtrovat z nativních <xref:System.Windows.DataObject.GetFormats%28System.Boolean%29> datových <xref:System.Windows.DataObject.GetDataPresent%28System.String%2CSystem.Boolean%29> formátů voláním metody `autoConvert` nebo a `false`určením parametru jako.  Při přidávání dat do datového objektu pomocí <xref:System.Windows.DataObject.SetData%28System.String%2CSystem.Object%2CSystem.Boolean%29> metody může být automatický převod dat zakázán `autoConvert` nastavením parametru na `false`.  
  
<a name="Working_with_Data_Objects"></a>   
## <a name="working-with-data-objects"></a>Práce s datovými objekty  
 Tato část popisuje běžné techniky pro vytváření a práci s datovými objekty.  
  
### <a name="creating-new-data-objects"></a>Vytváření nových datových objektů  
 Třída poskytuje několik přetížených konstruktorů, které usnadňují vyplnění nové <xref:System.Windows.DataObject> instance s jednou dvojicí dat nebo formátu dat. <xref:System.Windows.DataObject>  
  
 Následující příklad kódu vytvoří nový datový objekt a pomocí jednoho z přetížených konstruktorů <xref:System.Windows.DataObject.%23ctor%2A>(<xref:System.Windows.DataObject.%23ctor(System.String,System.Object)>) inicializuje datový objekt s řetězcem a zadaným formátem dat.  V tomto případě je formát dat určen řetězcem; <xref:System.Windows.DataFormats> Třída poskytuje sadu předem definovaných řetězců typu. Automatické konverze uložených dat je ve výchozím nastavení povolená.  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_typestring)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_typestring)]  
  
 Další příklady kódu, který vytváří datový objekt, najdete v tématu [vytvoření datového objektu](how-to-create-a-data-object.md).  
  
### <a name="storing-data-in-multiple-formats"></a>Ukládání dat v několika formátech  
 Jeden datový objekt může ukládat data v několika formátech.   Strategické použití více datových formátů v rámci jednoho datového objektu potenciálně umožňuje, aby datový objekt byl spotřební v širší škále cílů přetažení, než kdyby bylo možné znázornit pouze jeden datový formát.  Všimněte si, že obecně musí být zdroj přetažení nezávislá o datových formátech, které jsou spotřební, a to potenciálními cíli přetažení.  
  
 Následující příklad ukazuje, jak použít <xref:System.Windows.DataObject.SetData%28System.String%2CSystem.Object%29> metodu pro přidání dat do datového objektu v několika formátech.  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_StoreMultipleFormats](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_storemultipleformats)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_StoreMultipleFormats](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_storemultipleformats)]  
  
### <a name="querying-a-data-object-for-available-formats"></a>Dotazování datového objektu pro dostupné formáty  
 Vzhledem k tomu, že jeden datový objekt může obsahovat libovolný počet datových formátů, datové objekty zahrnují zařízení pro načtení seznamu dostupných formátů dat.  
  
 Následující příklad kódu používá <xref:System.Windows.DataObject.GetFormats%2A> přetížení k získání pole řetězců, ve kterém jsou všechny datové formáty dostupné v datovém objektu (nativní a automaticky převáděný).  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getalldataformats)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getalldataformats)]  
  
 Další příklady kódu, které dotazují datový objekt pro dostupné formáty dat, naleznete v tématu [seznam formátů dat v datovém objektu](how-to-list-the-data-formats-in-a-data-object.md).  Příklady dotazování datového objektu na přítomnost konkrétního datového formátu naleznete v tématu [určení, zda je v datovém objektu přítomen formát dat](how-to-determine-if-a-data-format-is-present-in-a-data-object.md).  
  
### <a name="retrieving-data-from-a-data-object"></a>Načítání dat z datového objektu  
 Načítání dat z datového objektu v konkrétním formátu jednoduše zahrnuje volání jedné z <xref:System.Windows.DataObject.GetData%2A> metod a určení požadovaného formátu dat.  Jednu z <xref:System.Windows.DataObject.GetDataPresent%2A> metod lze použít ke kontrole přítomnosti konkrétního formátu dat.  <xref:System.Windows.DataObject.GetData%2A>Vrátí data v <xref:System.Object>, v závislosti na formátu dat, tento objekt lze přetypovat na kontejner specifický pro typ.  
  
 Následující příklad kódu používá <xref:System.Windows.DataObject.GetDataPresent%28System.String%29> přetížení ke kontrole, zda je určený formát dat k dispozici (nativní nebo automaticky převáděný). Pokud je k dispozici zadaný formát, příklad načte data pomocí <xref:System.Windows.DataObject.GetData%28System.String%29> metody.  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getspecificdataformat)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getspecificdataformat)]  
  
 Další příklady kódu, který načítá data z datového objektu, najdete v tématu [načtení dat v konkrétním datovém formátu](how-to-retrieve-data-in-a-particular-data-format.md).  
  
### <a name="removing-data-from-a-data-object"></a>Odebrání dat z datového objektu  
 Data nelze z datového objektu odebrat přímo.  Chcete-li efektivně odebrat data z datového objektu, postupujte podle následujících kroků:  
  
1. Vytvořte nový datový objekt, který bude obsahovat pouze data, která chcete zachovat.  
  
2. "Zkopírujte" požadovaná data ze starého datového objektu do nového datového objektu.  Chcete-li zkopírovat data, použijte jednu z <xref:System.Windows.DataObject.GetData%2A> metod k <xref:System.Object> načtení obsahující nezpracovaná data a <xref:System.Windows.DataObject.SetData%2A> pak použijte jednu z metod k přidání dat do nového datového objektu.  
  
3. Nahraďte starý datový objekt novým.  
  
> [!NOTE]
> <xref:System.Windows.DataObject.SetData%2A> Metody přidávají data pouze do datového objektu; nenahrazují data, a to ani v případě, že jsou data a formát dat přesně stejné jako předchozí volání. Volání <xref:System.Windows.DataObject.SetData%2A> dvakrát pro stejná data a formát dat bude mít za následek, že se formát dat nebo dat v datovém objektu objeví dvakrát.
