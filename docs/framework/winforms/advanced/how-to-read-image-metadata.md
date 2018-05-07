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
ms.openlocfilehash: 92ce4eb8d51fbd25f9a129a629dc47bfb9941f34
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-read-image-metadata"></a>Postupy: Čtení metadat obrázku
Některé soubory, image obsahovat metadata, která si můžete přečíst určit funkce bitové kopie. Digitální fotografie může například obsahovat metadata, která si můžete přečíst k určení značku a model fotoaparátu používá k zachycení bitové kopie. S [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], si můžete přečíst metadata existujícího a novými metadaty je také možné zapsat do souborů obrázků.  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] ukládá jednotlivých druhem metadata v <xref:System.Drawing.Imaging.PropertyItem> objektu. Můžete si přečíst <xref:System.Drawing.Image.PropertyItems%2A> vlastnost <xref:System.Drawing.Image> objekt, který chcete načíst všechny metadat ze souboru. <xref:System.Drawing.Image.PropertyItems%2A> Vlastnost vrací pole <xref:System.Drawing.Imaging.PropertyItem> objekty.  
  
 A <xref:System.Drawing.Imaging.PropertyItem> objekt má následující čtyři vlastnosti: `Id`, `Value`, `Len`, a `Type`.  
  
## <a name="id"></a>ID  
 Značky, který identifikuje položky metadat. Některé hodnoty, které lze přiřadit k <xref:System.Drawing.Imaging.PropertyItem.Id%2A> jsou uvedeny v následující tabulce.  
  
|Šestnáctkové hodnoty|Popis|  
|-----------------------|-----------------|  
|0x0320<br /><br /> 0x010F<br /><br /> 0x0110<br /><br /> 0x9003<br /><br /> 0x829A<br /><br /> 0x5090<br /><br /> 0x5091|Název bitové kopie<br /><br /> Výrobce zařízení<br /><br /> Model zařízení<br /><br /> ExifDTOriginal<br /><br /> EXIF ohrožení čas<br /><br /> Tabulka světlostí<br /><br /> Tabulka Chrominance|  
  
## <a name="value"></a>Hodnota  
 Pole hodnot. Formát hodnoty je dáno <xref:System.Drawing.Imaging.PropertyItem.Type%2A> vlastnost.  
  
## <a name="len"></a>Len  
 Délka pole hodnot (v bajtech) na kterou odkazuje <xref:System.Drawing.Imaging.PropertyItem.Value%2A> vlastnost.  
  
## <a name="type"></a>Typ  
 Datový typ hodnoty v poli, na kterou odkazuje `Value` vlastnost. Formáty indikován `Type` v následující tabulce jsou uvedeny hodnoty vlastností  
  
|Číselná hodnota|Popis|  
|-------------------|-----------------|  
|1|A `Byte`|  
|2|Pole `Byte` objekty kódovaná jako ASCII|  
|3|16bitové celé číslo|  
|4|32bitové celé číslo|  
|5|O pole dvou `Byte` objekty, které představují racionální číslo|  
|6|Nepoužívá se|  
|7|Nedefinovaná|  
|8|Nepoužívá se|  
|9|`SLong`|  
|10|`SRational`|  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 Následující příklad kódu přečte a zobrazí sedm kusy metadata v souboru `FakePhoto.jpg`. Druhá položka vlastnost (index 1) v seznamu má <xref:System.Drawing.Imaging.PropertyItem.Id%2A> 0x010F (výrobce zařízení) a <xref:System.Drawing.Imaging.PropertyItem.Type%2A> 2 (pole bajtů s kódováním ASCII). Příklad kódu zobrazuje hodnota této vlastnosti položky.  
  
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
 [!code-csharp[System.Drawing.WorkingWithImages#51](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#51)]
 [!code-vb[System.Drawing.WorkingWithImages#51](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#51)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 V předchozím příkladu je určen k použití s modelem Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události. Zpracování formuláře <xref:System.Windows.Forms.Control.Paint> událostí a vložte tento kód do obslužné rutiny události Malování. Je třeba nahradit `FakePhoto.jpg` s název bitové kopie a cesta platné na systém a import `System.Drawing.Imaging` oboru názvů.  
  
## <a name="see-also"></a>Viz také  
 [Obrázky, rastrové obrázky a metasoubory](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 [Práce s obrázky, rastrovými obrázky, ikonami a metasoubory](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
