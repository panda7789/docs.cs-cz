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
ms.openlocfilehash: e2b56175e625281a920c390e5feb4238e3cb7f44
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182522"
---
# <a name="how-to-read-image-metadata"></a>Postupy: Čtení metadat obrázku

Některé obrazové soubory obsahují metadata, která můžete číst, abyste určili vlastnosti obrazu. Digitální fotografie může například obsahovat metadata, která můžete číst, abyste určili způsob a model fotoaparátu použitého k zachycení obrazu. Pomocí gdi+ můžete číst existující metadata a můžete také zapisovat nová metadata do obrazových souborů.

GDI+ ukládá jednotlivé části metadat <xref:System.Drawing.Imaging.PropertyItem> v objektu. Můžete číst <xref:System.Drawing.Image.PropertyItems%2A> vlastnost objektu <xref:System.Drawing.Image> načíst všechna metadata ze souboru. Vlastnost <xref:System.Drawing.Image.PropertyItems%2A> vrátí pole <xref:System.Drawing.Imaging.PropertyItem> objektů.

Objekt <xref:System.Drawing.Imaging.PropertyItem> má následující čtyři `Id`vlastnosti: , `Value`, `Len`a `Type`.

## <a name="id"></a>ID

Značka, která identifikuje položku metadat. Některé hodnoty, ke <xref:System.Drawing.Imaging.PropertyItem.Id%2A> kterým lze přiřadit, jsou uvedeny v následující tabulce:

|Šestnáctková hodnota|Popis|
|-----------------------|-----------------|
|0x0320<br /><br /> 0x010F<br /><br /> 0x0110<br /><br /> 0x9003<br /><br /> 0x829A<br /><br /> 0x5090<br /><br /> 0x5091|Název obrázku<br /><br /> Výrobce zařízení<br /><br /> Model vybavení<br /><br /> ExifDTOriginal<br /><br /> Exif doba expozice<br /><br /> Stůl jasu<br /><br /> Tabulka chrominance|

## <a name="value"></a>Hodnota

Pole hodnot. Formát hodnot je určen vlastností. <xref:System.Drawing.Imaging.PropertyItem.Type%2A>

## <a name="len"></a>Len

Délka (v bajtů) pole hodnot, na <xref:System.Drawing.Imaging.PropertyItem.Value%2A> které poukazuje vlastnost.

## <a name="type"></a>Typ

Datový typ hodnot v poli, na `Value` které je vlastnost í, je datový. Formáty označené hodnotami `Type` vlastností jsou uvedeny v následující tabulce:

|Číselná hodnota|Popis|
|-------------------|-----------------|
|1|Položka `Byte`.|
|2|Pole `Byte` objektů kódovaných jako ASCII|
|3|Šestnáctibitové celé číslo|
|4|32bitové celé číslo|
|5|Pole dvou `Byte` objektů, které představují racionální číslo|
|6|Nepoužívá se.|
|7|Nedefinované|
|8|Nepoužívá se.|
|9|`SLong`|
|10|`SRational`|

## <a name="example"></a>Příklad
  
Následující příklad kódu přečte a zobrazí sedm kusů `FakePhoto.jpg`metadat v souboru . Druhá položka vlastnosti (index 1) <xref:System.Drawing.Imaging.PropertyItem.Id%2A> v seznamu má 0x010F (výrobce zařízení) a <xref:System.Drawing.Imaging.PropertyItem.Type%2A> 2 (bajtové pole kódované ASCII). Příklad kódu zobrazuje hodnotu této položky vlastnosti.

[!code-csharp[System.Drawing.WorkingWithImages#51](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#51)]
[!code-vb[System.Drawing.WorkingWithImages#51](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#51)]

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

## <a name="compiling-the-code"></a>Probíhá kompilace kódu

Předchozí příklad je určen pro použití s windows <xref:System.Windows.Forms.PaintEventArgs> `e`forms a vyžaduje <xref:System.Windows.Forms.Control.Paint> , což je parametr obslužné rutiny události. Zpracovat <xref:System.Windows.Forms.Control.Paint> událost formuláře a vložit tento kód do obslužné rutiny události malování. Je nutné `FakePhoto.jpg` nahradit název obrázku a cestu platnou v systému a importovat obor `System.Drawing.Imaging` názvů.

## <a name="see-also"></a>Viz také

- [Obrázky, rastrové obrázky a metasoubory](images-bitmaps-and-metafiles.md)
- [Práce s obrázky, rastrovými obrázky, ikonami a metasoubory](working-with-images-bitmaps-icons-and-metafiles.md)
