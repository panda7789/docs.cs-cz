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
ms.openlocfilehash: 8294bc6596c408160a50d9d7d5e6154f66025c73
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2019
ms.locfileid: "70988561"
---
# <a name="how-to-read-image-metadata"></a>Postupy: Čtení metadat obrázku
Některé soubory obrázků obsahují metadata, která lze číst k určení funkcí obrázku. Digitální fotografie například může obsahovat metadata, která lze číst a určit tak model a model kamery použité k zachycení bitové kopie. Pomocí rozhraní GDI+ si můžete přečíst existující metadata a můžete také zapisovat nová metadata do souborů obrázků.  
  
 GDI+ ukládá jednotlivé části metadat do <xref:System.Drawing.Imaging.PropertyItem> objektu. Můžete číst <xref:System.Drawing.Image.PropertyItems%2A> vlastnost <xref:System.Drawing.Image> objektu pro načtení všech metadat ze souboru. <xref:System.Drawing.Image.PropertyItems%2A> Vlastnost vrací<xref:System.Drawing.Imaging.PropertyItem> pole objektů.  
  
 `Id` `Value` `Len`Objekt má následující čtyři vlastnosti:, ,`Type`a. <xref:System.Drawing.Imaging.PropertyItem>  
  
## <a name="id"></a>Id  
 Značka, která identifikuje položku metadat. V následující tabulce jsou uvedeny některé hodnoty <xref:System.Drawing.Imaging.PropertyItem.Id%2A> , které lze přiřadit k.  
  
|Hexadecimální hodnota|Popis|  
|-----------------------|-----------------|  
|0x0320<br /><br /> 0x010F<br /><br /> 0x0110<br /><br /> 0x9003<br /><br /> 0x829A<br /><br /> 0x5090<br /><br /> 0x5091|Název obrázku<br /><br /> Výrobce zařízení<br /><br /> Model vybavení<br /><br /> ExifDTOriginal<br /><br /> Doba expozice EXIF<br /><br /> Světlá tabulka<br /><br /> Tabulka chrominance|  
  
## <a name="value"></a>Value  
 Pole hodnot. Formát hodnot je určen <xref:System.Drawing.Imaging.PropertyItem.Type%2A> vlastností.  
  
## <a name="len"></a>Funkce  
 Délka (v bajtech) pole hodnot, na <xref:System.Drawing.Imaging.PropertyItem.Value%2A> které se odkazuje vlastnost.  
  
## <a name="type"></a>type  
 Datový typ hodnot v poli, na který `Value` odkazuje vlastnost. Formáty uvedené `Type` v hodnotách vlastností jsou uvedeny v následující tabulce.  
  
|Číselná hodnota|Popis|  
|-------------------|-----------------|  
|1|A `Byte`|  
|2|Pole `Byte` objektů kódovaných jako ASCII|  
|3|16bitové celé číslo|  
|4|32 celé číslo|  
|5|Pole dvou `Byte` objektů, které reprezentují racionální číslo|  
|6|Nepoužívá se|  
|7|Nedefinováno|  
|8|Nepoužívá se|  
|9|`SLong`|  
|10|`SRational`|  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 Následující příklad kódu načte a zobrazí sedm částí metadat v souboru `FakePhoto.jpg`. Druhá položka vlastnosti (index 1) v seznamu má <xref:System.Drawing.Imaging.PropertyItem.Id%2A> 0x010F (výrobce vybavení) a <xref:System.Drawing.Imaging.PropertyItem.Type%2A> 2 (bajtové pole s kódováním ASCII). V příkladu kódu se zobrazí hodnota této položky vlastnosti.  
  
 Kód vytváří výstup podobný následujícímu:  
 
```output
 Property Item 0
  
 id: 0x320
  
 type: 2
 
 length: 16 bytes 
  
 Property Item 1
  
 id: 0x10f
  
 type: 2 
  
 length: 17 bytes
  
 Property Item 2
  
 id: 0x110
  
 type: 2
  
 length: 7 bytes
  
 Property Item 3
  
 id: 0x9003
  
 type: 2
  
 length: 20 bytes
  
 Property Item 4
  
 id: 0x829a
  
 type: 5
  
 length: 8 bytes
  
 Property Item 5
  
 id: 0x5090
  
 type: 3
  
 length: 128 bytes
  
 Property Item 6
  
 id: 0x5091
  
 type: 3
  
 length: 128 bytes
  
 The equipment make is Northwind Camera.
 ```
  
### <a name="code"></a>Kód  
 [!code-csharp[System.Drawing.WorkingWithImages#51](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#51)]
 [!code-vb[System.Drawing.WorkingWithImages#51](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#51)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Předchozí příklad je navržen pro použití s model Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což <xref:System.Windows.Forms.Control.Paint> je parametr obslužné rutiny události. Zpracujte <xref:System.Windows.Forms.Control.Paint> událost formuláře a vložte tento kód do obslužné rutiny události Paint. Je nutné nahradit `FakePhoto.jpg` názvem Image a cestou platnými v systému a `System.Drawing.Imaging` importovat obor názvů.  
  
## <a name="see-also"></a>Viz také:

- [Obrázky, rastrové obrázky a metasoubory](images-bitmaps-and-metafiles.md)
- [Práce s obrázky, rastrovými obrázky, ikonami a metasoubory](working-with-images-bitmaps-icons-and-metafiles.md)
