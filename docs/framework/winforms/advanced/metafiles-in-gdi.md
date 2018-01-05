---
title: "Metasoubory v rozhraní GDI+"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [Windows Forms], metafiles
- GDI+, metafiles
- metafiles
ms.assetid: 51da872c-c783-440f-8bf6-1e580a966c31
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2b9d378f82b2a7edca00fedaacdcc0fca179c5a0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="metafiles-in-gdi"></a>Metasoubory v rozhraní GDI+
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]poskytuje <xref:System.Drawing.Imaging.Metafile> třídy, aby mohli zaznamenat a zobrazení metasouborů. Metasoubory, označované taky jako bitovou kopii vektoru je image, která je uložena jako posloupnost kreslení příkazy a nastavení. Příkazy a nastavení popsané v <xref:System.Drawing.Imaging.Metafile> objekt můžete uložené v paměti nebo uložit do souboru nebo datový proud.  
  
## <a name="metafile-formats"></a>Formáty metasouborů  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]můžete zobrazit metasoubory, která jsou uložená v následujících formátech:  
  
-   Formát WMF (WMF)  
  
-   EMF (Enhanced Metafile)  
  
-   EMF +  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]můžete zaznamenat metasoubory v formáty EMF a EMF +, ale není ve formátu WMF.  
  
 EMF + je rozšíření EMF, která umožňuje [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] záznamy uložit. Existují dvě varianty EMF + format: EMF + pouze a duální EMF +. EMF + pouze metasoubory obsahovat pouze [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] záznamy. Takové metasoubory lze zobrazit [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] , ale nejsou nástrojem [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]. Metasoubory EMF + duální obsahovat [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] a [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] záznamy. Každý [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] záznamů v duální EMF + metafile je spárován s náhradní [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] záznamu. Takové metasoubory lze zobrazit [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] nebo [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)].  
  
 Následující příklad zobrazuje metafile, který byl dříve uložili jako soubor. S jeho levého horního rohu na se zobrazí metafile (100, 100).  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#21)]  
  
## <a name="see-also"></a>Viz také  
 [Obrázky, rastrové obrázky a metasoubory](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)
