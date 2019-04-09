---
title: 'Postupy: Čtení metadat obrázku'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- metadata [Windows Forms], property item
- metadata [Windows Forms], reading image
ms.assetid: 72ec0b31-0be7-444a-9575-1dbcb864e0be
ms.openlocfilehash: 0a53e9b9d23c03715bf3088a4ae8577a39527995
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59173612"
---
# <a name="how-to-read-image-metadata"></a>Postupy: Čtení metadat obrázku
Některé soubory obrázku obsahují metadata, která si můžete přečíst určit funkce bitové kopie. Digitální fotografie může například obsahovat metadata, která si můžete přečíst k určení značku a model fotoaparátu/kamery, používá k zachycení bitové kopie. S [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]existující metadata mohou číst a můžete je zapsat také nová metadata do souborů obrázků.  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] ukládá jednotlivé část metadata <xref:System.Drawing.Imaging.PropertyItem> objektu. Si můžete přečíst <xref:System.Drawing.Image.PropertyItems%2A> vlastnost <xref:System.Drawing.Image> objektu k načtení všechna metadata ze souboru. <xref:System.Drawing.Image.PropertyItems%2A> Vlastnost vrací pole <xref:System.Drawing.Imaging.PropertyItem> objekty.  
  
 A <xref:System.Drawing.Imaging.PropertyItem> objekt má následující čtyři vlastnosti: `Id`, `Value`, `Len`, a `Type`.  
  
## <a name="id"></a>ID  
 Značka, která identifikuje položku metadat. Některé hodnoty, které je možné přiřadit <xref:System.Drawing.Imaging.PropertyItem.Id%2A> jsou uvedeny v následující tabulce.  
  
|Šestnáctková hodnota|Popis|  
|-----------------------|-----------------|  
|0x0320<br /><br /> 0x010F<br /><br /> 0x0110<br /><br /> 0x9003<br /><br /> 0x829A<br /><br /> 0x5090<br /><br /> 0x5091|Název bitové kopie<br /><br /> Výrobce OEM<br /><br /> Model zařízení<br /><br /> ExifDTOriginal<br /><br /> Chcete zkrátit dobu expozice EXIF<br /><br /> Tabulka světlosti<br /><br /> Chrominance tabulky|  
  
## <a name="value"></a>Hodnota  
 Pole hodnot. Formát hodnoty je určeno <xref:System.Drawing.Imaging.PropertyItem.Type%2A> vlastnost.  
  
## <a name="len"></a>Délka  
 Délka (v bajtech) pole hodnot, na které odkazují <xref:System.Drawing.Imaging.PropertyItem.Value%2A> vlastnost.  
  
## <a name="type"></a>Type  
 Datový typ hodnoty v poli na které odkazují `Value` vlastnost. Formáty indikován `Type` v následující tabulce jsou uvedeny hodnoty vlastností  
  
|Číselná hodnota|Popis|  
|-------------------|-----------------|  
|1|OBJEKT `Byte`|  
|2|Pole `Byte` objekty kódováním ASCII|  
|3|16bitové celé číslo|  
|4|32bitové celé číslo|  
|5|Pole dvou `Byte` objekty, které představují racionální číslo|  
|6|Nepoužívá se|  
|7|Nedefinováno|  
|8|Nepoužívá se|  
|9|`SLong`|  
|10|`SRational`|  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 Následující příklad kódu načte a zobrazí sedmi částí metadat v souboru `FakePhoto.jpg`. Druhá položka vlastnosti (index 1) v seznamu má <xref:System.Drawing.Imaging.PropertyItem.Id%2A> 0x010F (výrobce) a <xref:System.Drawing.Imaging.PropertyItem.Type%2A> 2 (pole bajtů s kódováním ASCII). Příklad kódu zobrazí hodnotu této vlastnosti položky.  
  
 Kód vytvoří výstup podobný následujícímu:  
  
 `Property Item 0`  
  
 `id: 0x320`  
  
 `type: 2`  
  
 `length: 16 bytes`  
  
 `Property Item 1`  
  
 `id: 0x10f`  
  
 `type: 2`  
  
 `length: 17 bytes`  
  
 `Property Item 2`  
  
 `id: 0x110`  
  
 `type: 2`  
  
 `length: 7 bytes`  
  
 `Property Item 3`  
  
 `id: 0x9003`  
  
 `type: 2`  
  
 `length: 20 bytes`  
  
 `Property Item 4`  
  
 `id: 0x829a`  
  
 `type: 5`  
  
 `length: 8 bytes`  
  
 `Property Item 5`  
  
 `id: 0x5090`  
  
 `type: 3`  
  
 `length: 128 bytes`  
  
 `Property Item 6`  
  
 `id: 0x5091`  
  
 `type: 3`  
  
 `length: 128 bytes`  
  
 `The equipment make is Northwind Camera.`  
  
### <a name="code"></a>Kód  
 [!code-csharp[System.Drawing.WorkingWithImages#51](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#51)]
 [!code-vb[System.Drawing.WorkingWithImages#51](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#51)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 V předchozím příkladu je určený k použití pomocí Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události. Zpracování formuláře <xref:System.Windows.Forms.Control.Paint> událostí a vložte tento kód do obslužné rutiny události Malování. Je třeba nahradit `FakePhoto.jpg` název image a cesta platné na systém a import `System.Drawing.Imaging` oboru názvů.  
  
## <a name="see-also"></a>Viz také:

- [Obrázky, rastrové obrázky a metasoubory](images-bitmaps-and-metafiles.md)
- [Práce s obrázky, rastrovými obrázky, ikonami a metasoubory](working-with-images-bitmaps-icons-and-metafiles.md)
