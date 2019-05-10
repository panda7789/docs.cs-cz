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
ms.openlocfilehash: 1e573a3fd175d977d437933d5588c1795851ddc6
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64627360"
---
# <a name="data-and-data-objects"></a>Data a datové objekty
Data, která jsou přenášena jako součást operace přetažení myší se ukládají do datového objektu.  Datový objekt koncepčně, obsahuje jeden nebo více následující páry:  
  
- <xref:System.Object> Obsahující skutečná data.  
  
- Odpovídající identifikátor formát data.  
  
 Vlastní data může obsahovat cokoli, co může být reprezentována jako základ <xref:System.Object>.  Odpovídající formát dat je řetězec nebo <xref:System.Type> , který poskytuje informace o co formátování dat probíhá.  Datové objekty podporují hostování více párů formátu data/dat; To umožňuje jednoho datového objektu poskytující data ve více formátech.  
  
<a name="Data_and_Data_Objects"></a>   
## <a name="data-objects"></a>Datové objekty  
 Musí implementovat všechny datové objekty <xref:System.Windows.IDataObject> rozhraní, které poskytuje následující standardní sady metod, které umožňují a usnadnění datové přenosy.  
  
|Metoda|Souhrn|  
|------------|-------------|  
|<xref:System.Windows.IDataObject.GetData%2A>|Načte objekt data ve formátu zadaná data.|  
|<xref:System.Windows.IDataObject.GetDataPresent%2A>|Zkontroluje, zda je k dispozici v data, nebo lze převést na zadaný formát.|  
|<xref:System.Windows.IDataObject.GetFormats%2A>|Vrátí seznam hodnot formáty, které je uložen v dat tohoto datového objektu nebo lze převést na.|  
|<xref:System.Windows.IDataObject.SetData%2A>|V tomto objektu data ukládá zadaná data.|  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] poskytuje základní implementaci <xref:System.Windows.IDataObject> v <xref:System.Windows.DataObject> třídy. Stock <xref:System.Windows.DataObject> pro spoustu běžných scénářů přenos dat stačí třídy.  
  
 Existuje několik předdefinovaných formátů, například rastrový obrázek, sdíleného svazku clusteru, soubor, HTML, formátu RTF, řetězec, text a zvuk. Informace o předdefinovaných datových formátů, opatřeného [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], najdete v článku <xref:System.Windows.DataFormats> tématu referenční třídy.  
  
 Datové objekty běžně zahrnují zařízení automaticky převodu dat uložených v jednoho formátu do jiného formátu při extrahování dat Toto zařízení se označuje jako automatický převod. Při dotazování na data formátů v datovém objektu, je automaticky převoditelné datových formátů filtrovat z nativních datových formátů voláním <xref:System.Windows.DataObject.GetFormats%28System.Boolean%29> nebo <xref:System.Windows.DataObject.GetDataPresent%28System.String%2CSystem.Boolean%29> metoda a zadáte `autoConvert` parametr jako `false`.  Při přidání dat do datového objektu s <xref:System.Windows.DataObject.SetData%28System.String%2CSystem.Object%2CSystem.Boolean%29> metoda automatický převod dat můžete zakázáno nastavením `autoConvert` parametr `false`.  
  
<a name="Working_with_Data_Objects"></a>   
## <a name="working-with-data-objects"></a>Práce s objekty dat  
 Tato část popisuje běžné postupy pro vytváření a práci s datovými objekty.  
  
### <a name="creating-new-data-objects"></a>Vytvoření nové datové objekty  
 <xref:System.Windows.DataObject> Třída poskytuje několik přetížených konstruktorů, které usnadňují sestavování nové <xref:System.Windows.DataObject> instance s párem formátu jeden data nebo data.  
  
 Následující příklad kódu vytvoří nový objekt dat a používá jednu z přetížených konstruktorů <xref:System.Windows.DataObject.%23ctor%2A>(<xref:System.Windows.DataObject.%23ctor(System.String,System.Object)>) k inicializaci dat objektu řetězce a zadaného data formátu.  V takovém případě formát dat je zadán řetězcem; <xref:System.Windows.DataFormats> třída poskytuje sadu předdefinovaných typů řetězců. Ve výchozím nastavení je povolený automatický převod uložená data.  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_typestring)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_typestring)]  
  
 Další příklady kódu, který vytvoří objekt dat najdete v tématu [vytvoření datového objektu](how-to-create-a-data-object.md).  
  
### <a name="storing-data-in-multiple-formats"></a>Ukládání dat ve více formátech  
 Single – datový objekt je možné k ukládání dat v různých formátech.   Strategické využívání několika datových formátů v rámci jednoho datového objektu potenciálně díky datový objekt použití širší rozsah cíle přetažení než pokud pouze jeden datový formát můžou být reprezentované.  Všimněte si, že obecně platí, přetáhněte zdroj musí být nezávislá o formátech dat, které jsou použitelné tak potenciální cíle přetažení.  
  
 Následující příklad ukazuje způsob použití <xref:System.Windows.DataObject.SetData%28System.String%2CSystem.Object%29> metoda pro přidání dat na datový objekt v různých formátech.  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_StoreMultipleFormats](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_storemultipleformats)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_StoreMultipleFormats](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_storemultipleformats)]  
  
### <a name="querying-a-data-object-for-available-formats"></a>Dotazování na datový objekt k dispozici formátů  
 Protože jednoho datového objektu může obsahovat libovolný počet datových formátů, zahrnují datové objekty zařízení pro načtení seznamu dostupných datových formátů.  
  
 Následující příklad kódu používá <xref:System.Windows.DataObject.GetFormats%2A> přetížení pro získání pole řetězců, které označuje všechny datových formátů do datového objektu (nativní i o automatický převod).  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getalldataformats)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getalldataformats)]  
  
 Další příklady kódu, který se dotazuje datový objekt k dispozici data formátů naleznete v tématu [seznam datových formátů v datovém objektu](how-to-list-the-data-formats-in-a-data-object.md).  Příklady dotazů na datový objekt na přítomnost konkrétním datovém formátu naleznete v tématu [určení, zda formát dat je k dispozici v datovém objektu](how-to-determine-if-a-data-format-is-present-in-a-data-object.md).  
  
### <a name="retrieving-data-from-a-data-object"></a>Načítání dat z datového objektu  
 Načítání dat z objektu dat v určitém formátu jednoduše zahrnuje volání jedné z <xref:System.Windows.DataObject.GetData%2A> metody a určení formátu požadovaná data.  Jeden z <xref:System.Windows.DataObject.GetDataPresent%2A> metody slouží ke kontrole přítomnosti konkrétním datovém formátu.  <xref:System.Windows.DataObject.GetData%2A> vrací data do <xref:System.Object>; v závislosti na formát dat, tento objekt lze převést na typ konkrétní kontejner.  
  
 Následující příklad kódu používá <xref:System.Windows.DataObject.GetDataPresent%28System.String%29> přetížení ke kontrole, jestli zadaný datový formát je k dispozici (nativní nebo automatický převod). Pokud zadaný formát je k dispozici, příklad načte data s využitím <xref:System.Windows.DataObject.GetData%28System.String%29> metody.  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getspecificdataformat)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getspecificdataformat)]  
  
 Další příklady kódu, který načítá data z datového objektu, naleznete v tématu [načíst Data v konkrétním datovém formátu](how-to-retrieve-data-in-a-particular-data-format.md).  
  
### <a name="removing-data-from-a-data-object"></a>Odebrání dat z datového objektu  
 Data nelze odebrat přímo z datového objektu.  Efektivně odebrat data z datového objektu, postupujte podle těchto kroků:  
  
1. Vytvořte nový objekt data, která bude obsahovat pouze data, která chcete zachovat.  
  
2. "Kopie" požadovaným datům z původního objektu dat na nový datový objekt.  Ke zkopírování dat, použijte jednu z <xref:System.Windows.DataObject.GetData%2A> metody pro načtení <xref:System.Object> obsahující nezpracovaná data a pak použijte jednu z <xref:System.Windows.DataObject.SetData%2A> metody pro přidání dat na nový datový objekt.  
  
3. Nahraďte novým starý datový objekt.  
  
> [!NOTE]
>  <xref:System.Windows.DataObject.SetData%2A> Metody pouze přidat data do datového objektu; nenahrazují data, i v případě, že data a formát dat jsou stejné jako předchozí volání. Volání <xref:System.Windows.DataObject.SetData%2A> dvakrát pro stejné data a data formátu způsobí ve formátu data a data byla vyžadována jeho přítomnost dvakrát za datový objekt.
