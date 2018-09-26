---
title: Programovatelnost Store metadat
ms.date: 03/30/2017
ms.assetid: 5b613661-f3f9-4e07-8e88-28c9ea2fd8f8
ms.openlocfilehash: 9f30fcdac131b8749a4d165875b9bbb584542843
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/26/2018
ms.locfileid: "47209857"
---
# <a name="metadata-store-programmability"></a>Programovatelnost Store metadat
Metadata úložiště je [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)] funkce, která umožňuje přidružení libovolného metadat ve formě CLR atributy pro typy v době běhu. To umožňuje volné párování mezi běhové komponenty a jejich protějšky v době návrhu, jakož i změnit komponenty doby návrhu, aniž by to ovlivnilo modul runtime. Vzorek ukazuje, jak programovat proti úložišti metadat s použitím atributů typu za běhu, u kterého jsme nemají žádnou kontrolu nad zdroji. Terminologie obvykle používá je, že hostitelské aplikace registruje metadata pro sadu typů.  
  
 V rámci výstupu, můžete si všimnout atribut další, neočekávané <xref:System.Runtime.InteropServices.GuidAttribute>. Tím se přidá při používání metadat rozhraní API a nemá žádný vliv na spuštění ukázky.  
  
 V této ukázce:  
  
## <a name="demonstrates"></a>Demonstruje  
  
-   Uložit atribut vkládání pomocí metadat rozhraní API.  
  
-   Odložení metadat registrace pomocí mechanismu zpětného volání.  
  
## <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku
  
1.  Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení ProgrammingMetadataStore.sln.  
  
2.  Abyste mohli sestavit řešení, stiskněte kombinaci kláves CTRL + SHIFT + B.  
  
3.  Abyste mohli spustit řešení, stiskněte klávesu F5.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\MetadataStore`