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
ms.openlocfilehash: ff596dc7428c9d105a27999f216d33e735e35a22
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="data-and-data-objects"></a>Data a datové objekty
Data, která se přenáší v rámci operace přetažení myší uloženo v datovém objektu.  Datový objekt koncepčně, se skládá z jednoho nebo více dvojic následující:  
  
-   <xref:System.Object> Obsahující skutečná data.  
  
-   Odpovídající identifikátor formát data.  
  
 Samotná data se může skládat z všechno, co může být reprezentován jako na základní <xref:System.Object>.  Odpovídající formát dat je řetězec nebo <xref:System.Type> , který poskytuje informace, o co formátování dat je v.  Datové objekty podporují, hostování více párů formát dat nebo dat; To umožňuje jeden datový objekt k poskytnutí dat ve více formátech.  
  
<a name="Data_and_Data_Objects"></a>   
## <a name="data-objects"></a>Datové objekty  
 Všechny objekty data musí implementovat <xref:System.Windows.IDataObject> rozhraní, což poskytuje následující standardní sady metod, které umožňují a usnadnění přenos dat.  
  
|Metoda|Souhrn|  
|------------|-------------|  
|<xref:System.Windows.IDataObject.GetData%2A>|Načte objekt dat ve formátu, zadaná data.|  
|<xref:System.Windows.IDataObject.GetDataPresent%2A>|Zkontroluje, zda je k dispozici v dat, nebo lze převést na zadaný formát.|  
|<xref:System.Windows.IDataObject.GetFormats%2A>|Vrátí seznam hodnot formáty, které jsou uloženy v data v tomto objektu dat, nebo lze převést na.|  
|<xref:System.Windows.IDataObject.SetData%2A>|V tomto objektu data ukládá zadaná data.|  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] poskytuje základní implementaci <xref:System.Windows.IDataObject> v <xref:System.Windows.DataObject> třídy. Stock <xref:System.Windows.DataObject> třída je pro mnoho běžných scénářů přenosu dat dostatečné.  
  
 Existuje několik předdefinovaných formátů, jako je například rastrového obrázku, CSV, soubor, HTML, RTF, řetězec, text a zvuku. Informace o formátech předem definované datové součástí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], najdete v článku <xref:System.Windows.DataFormats> třída referenční téma.  
  
 Datové objekty běžně zahrnout do zařízení pro automaticky převodu dat uložených v jednoho formátu do jiného formátu při extrahování dat; Pokud tuto funkci se označuje jako automatický převod. Při dotazování na data formátů aplikace na datový objekt, je možné filtrovat formáty dat automaticky převoditelné z nativní data formátů voláním <xref:System.Windows.DataObject.GetFormats%28System.Boolean%29> nebo <xref:System.Windows.DataObject.GetDataPresent%28System.String%2CSystem.Boolean%29> metoda a se zadáním `autoConvert` parametr jako `false`.  Při přidání dat na datový objekt s <xref:System.Windows.DataObject.SetData%28System.String%2CSystem.Object%2CSystem.Boolean%29> metody automatického převodu dat může být zakázáno nastavením `autoConvert` parametru `false`.  
  
<a name="Working_with_Data_Objects"></a>   
## <a name="working-with-data-objects"></a>Práce s objekty dat  
 Tato část popisuje běžné techniky pro vytváření a práci s datových objektů.  
  
### <a name="creating-new-data-objects"></a>Vytváření nových objektů dat  
 <xref:System.Windows.DataObject> Třída poskytuje několik přetížené konstruktory, které usnadňují sestavování novou <xref:System.Windows.DataObject> instance dvojice formátu jednoho data nebo data.  
  
 Následující příklad kódu vytvoří nový objekt dat a používá jednu z přetížené konstruktory <xref:System.Windows.DataObject.%23ctor%2A>(<xref:System.Windows.DataObject.%23ctor(System.String,System.Object)>) k inicializaci objektu data s řetězec a formátu zadaná data.  V takovém případě formát dat je zadán řetězcem; <xref:System.Windows.DataFormats> třída poskytuje sadu předdefinovaných typ řetězce. Ve výchozím nastavení je povolen automatický převod uložená data.  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_typestring)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_typestring)]  
  
 Další příklady kódu, který vytvoří objekt dat najdete v tématu [vytvořit datový objekt](../../../../docs/framework/wpf/advanced/how-to-create-a-data-object.md).  
  
### <a name="storing-data-in-multiple-formats"></a>Ukládání dat ve více formátech  
 Single – datový objekt je možné ukládat data ve více formátech.   Strategické použití více formátů data v rámci jednoho datového objektu potenciálně umožňuje datový objekt použití širší rozsah cílů přemístění než pokud jenom jeden datový formát může být reprezentován.  Všimněte si, že obecně platí, musí být zdroje operace přetažení lhostejné o formáty dat, které jsou použití potenciální cílů umístění.  
  
 Následující příklad ukazuje způsob použití <xref:System.Windows.DataObject.SetData%28System.String%2CSystem.Object%29> metoda pro přidání dat na datový objekt ve více formátech.  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_StoreMultipleFormats](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_storemultipleformats)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_StoreMultipleFormats](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_storemultipleformats)]  
  
### <a name="querying-a-data-object-for-available-formats"></a>Dotaz na datový objekt k dispozici formátů  
 Protože jeden datový objekt může obsahovat libovolný počet formáty dat, zahrnují datové objekty zařízení pro načítání seznamu dostupných dat formátů.  
  
 Následující příklad kódu používá <xref:System.Windows.DataObject.GetFormats%2A> přetížení získat pole řetězců, které označuje všechny formáty dat v datovém objektu (nativní i pomocí automatický převod) k dispozici.  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getalldataformats)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getalldataformats)]  
  
 Další příklady kódu, který se dotazuje na datový objekt k dispozici data formátů naleznete v tématu [seznamu formáty dat v datovém objektu](../../../../docs/framework/wpf/advanced/how-to-list-the-data-formats-in-a-data-object.md).  Příklady dotazů na datový objekt na přítomnost formát konkrétní dat najdete v tématu [určit, zda formát dat je přítomen v datovém objektu](../../../../docs/framework/wpf/advanced/how-to-determine-if-a-data-format-is-present-in-a-data-object.md).  
  
### <a name="retrieving-data-from-a-data-object"></a>Načítání dat z dat objektu  
 Načítání dat z dat objektu v určitém formátu jednoduše zahrnuje volání jedné z <xref:System.Windows.DataObject.GetData%2A> metody a určení formátu požadovaným datům.  Jeden z <xref:System.Windows.DataObject.GetDataPresent%2A> metody lze kontrolovat přítomnost konkrétní datové formátu.  <xref:System.Windows.DataObject.GetData%2A> vrací data v <xref:System.Object>; v závislosti na formát dat, tento objekt lze převést na specifický kontejner.  
  
 Následující příklad kódu používá <xref:System.Windows.DataObject.GetDataPresent%28System.String%29> přetížení zkontrolujte, jestli je k dispozici zadaná data formátu (nativní nebo automatický převod). Pokud zadaný formát je k dispozici, příklad načte data pomocí <xref:System.Windows.DataObject.GetData%28System.String%29> metoda.  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getspecificdataformat)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getspecificdataformat)]  
  
 Další příklady kódu, který načte data z datového objektu najdete v tématu [načíst Data v určitém formátu dat](../../../../docs/framework/wpf/advanced/how-to-retrieve-data-in-a-particular-data-format.md).  
  
### <a name="removing-data-from-a-data-object"></a>Odebrání dat z datového objektu  
 Data nelze odebrat přímo z datového objektu.  Efektivně odebrat data z datového objektu, postupujte takto:  
  
1.  Vytvořte nový datový objekt, který bude obsahovat pouze data, která chcete zachovat.  
  
2.  "Kopie" k požadovaným datům z původního data objektu na nový datový objekt.  Ke zkopírování dat, použijte jednu z <xref:System.Windows.DataObject.GetData%2A> metody načíst <xref:System.Object> obsahující nezpracovaná data a potom použijte jednu z <xref:System.Windows.DataObject.SetData%2A> metody pro přidání dat na nový datový objekt.  
  
3.  Nahraďte starý datový objekt tímto novým připojením.  
  
> [!NOTE]
>  <xref:System.Windows.DataObject.SetData%2A> Metody přidat pouze data na datový objekt; nenahrazují data, i v případě dat a formát dat jsou stejné jako předchozí volání. Volání metody <xref:System.Windows.DataObject.SetData%2A> dvakrát pro stejný data a data formátu způsobí formát dat nebo dat probíhá dvakrát v objektu data.
