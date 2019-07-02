---
title: Metasoubory v rozhraní GDI+
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [Windows Forms], metafiles
- GDI+, metafiles
- metafiles
ms.assetid: 51da872c-c783-440f-8bf6-1e580a966c31
ms.openlocfilehash: df54289722cf12bad840722c6eafdaa43279a5dc
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2019
ms.locfileid: "67504582"
---
# <a name="metafiles-in-gdi"></a>Metasoubory v rozhraní GDI+
Poskytuje rozhraní GDI + <xref:System.Drawing.Imaging.Metafile> třídy, aby mohli zaznamenat a zobrazení metasouborů. Metasoubor zkratka bitovou kopii vektoru je obrázek, který se ukládá jako posloupnost kreslení příkazy a nastavení. Příkazy a nastavení popsané v <xref:System.Drawing.Imaging.Metafile> objektu lze uložit v paměti nebo uložit do souboru nebo datového proudu.  
  
## <a name="metafile-formats"></a>Formáty metasoubor  
 Rozhraní GDI + můžete zobrazení metasouborů uložené v následujících formátech:  
  
- Windows Metafile (WMF)  
  
- EMF (Enhanced Metafile)  
  
- EMF+  
  
 Rozhraní GDI + můžete zaznamenat metasoubory v EMF a EMF + formáty, ale není ve formátu WMF.  
  
 EMF + je rozšíření EMF, která umožňuje rozhraní GDI + záznamy mají být uloženy. Existují dvě varianty EMF + formát: EMF + pouze a EMF + duální. EMF + pouze metasoubory obsahuje pouze záznamy rozhraní GDI +. Takové metasoubory lze zobrazit pomocí GDI +, ale ne GDI. Metasoubory EMF + duální obsahovat rozhraní GDI + a GDI záznamů. Každý záznam rozhraní GDI + duální EMF + metasoubor je spárovaná s alternativní záznam GDI. Takové metasoubory lze zobrazit pomocí GDI + nebo GDI.  
  
 Následující příklad zobrazuje metasoubor dříve uložený jako soubor. Zobrazí se tento metasoubor pomocí jeho levého horního rohu na (100, 100).  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#21)]  
  
## <a name="see-also"></a>Viz také:

- [Obrázky, rastrové obrázky a metasoubory](images-bitmaps-and-metafiles.md)
