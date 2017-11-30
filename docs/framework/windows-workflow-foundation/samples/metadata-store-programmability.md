---
title: "Programovatelnosti úložiště metadat"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5b613661-f3f9-4e07-8e88-28c9ea2fd8f8
caps.latest.revision: "15"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3e0dfbfdcec6f07cd6106754943029965cd33c1f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="metadata-store-programmability"></a>Programovatelnosti úložiště metadat
Metadata úložiště je [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)] funkce, která umožňuje pro přidružení libovolný metadata, a to ve formě CLR atributy, typy za běhu. To umožňuje volné párování mezi komponenty Runtime a jejich protějšky v době návrhu a také možnost měnit součásti návrhu bez ovlivnění modulu runtime. Ukázka ukazuje, jak program proti úložišti metadat aplikací běhového typu zdroje, pro kterou jsme nemají žádnou kontrolu nad atributů. Terminologie obvykle používaných je, že hostitelskou aplikaci zaregistruje metadata pro sadu typů.  
  
 V rámci výstupu, můžete si povšimnout atribut další, neočekávané <!--zz <xref:System.Runtime.InteropServices.GUIDAttribute> --> `System.Runtime.InteropServices.GUIDAttribute`. Tím se přidá při použití metadat rozhraní API a nemá žádný vliv na spuštění ukázky.  
  
 Tento příklad znázorňuje:  
  
## <a name="demonstrates"></a>Demonstruje  
  
-   Atribut vkládání pomocí metadat ukládat rozhraní API.  
  
-   Odložení metadata registrace pomocí mechanismus zpětného volání.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení ProgrammingMetadataStore.sln.  
  
2.  Sestavte řešení, stiskněte CTRL + SHIFT + B.  
  
3.  Pokud chcete spustit řešení, stisknutím klávesy F5.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\MetadataStore`  
  
## <a name="see-also"></a>Viz také
