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
ms.openlocfilehash: 25ce3fdd98560aba0918431bb77d6f3f23a04784
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57722461"
---
# <a name="metafiles-in-gdi"></a>Metasoubory v rozhraní GDI+
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] poskytuje <xref:System.Drawing.Imaging.Metafile> třídy, aby mohli zaznamenat a zobrazení metasouborů. Metasoubor zkratka bitovou kopii vektoru je obrázek, který se ukládá jako posloupnost kreslení příkazy a nastavení. Příkazy a nastavení popsané v <xref:System.Drawing.Imaging.Metafile> objektu lze uložit v paměti nebo uložit do souboru nebo datového proudu.  
  
## <a name="metafile-formats"></a>Formáty metasoubor  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] můžete zobrazit metasoubory, které jsou uložené v následujících formátech:  
  
-   Windows Metafile (WMF)  
  
-   EMF (Enhanced Metafile)  
  
-   EMF+  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] můžete zaznamenat metasoubory v EMF a EMF + formáty, ale není ve formátu WMF.  
  
 EMF + je rozšíření EMF umožňující [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] záznamy mají být uloženy. Existují dvě varianty EMF + formát: EMF + pouze a EMF + duální. EMF + pouze metasoubory obsahovat pouze [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] záznamy. Tyto soubory lze zobrazit v [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] , ale ne za [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]. Metasoubory EMF + duální obsahovat [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] a [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] záznamy. Každý [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] záznam ve dvou EMF + metasoubor se páruje s oblastí alternativu [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] záznamu. Tyto soubory lze zobrazit v [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] nebo [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)].  
  
 Následující příklad zobrazuje metasoubor dříve uložený jako soubor. Zobrazí se tento metasoubor pomocí jeho levého horního rohu na (100, 100).  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#21)]  
  
## <a name="see-also"></a>Viz také:
- [Obrázky, rastrové obrázky a metasoubory](images-bitmaps-and-metafiles.md)
