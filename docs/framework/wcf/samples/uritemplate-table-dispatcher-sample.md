---
title: Ukázka dispečera tabulky UriTemplate
ms.date: 03/30/2017
ms.assetid: 3b32975d-ba90-4c5c-83bc-2fbb48f11c0c
ms.openlocfilehash: 9075d779b2ca2360c5ad28c3872c54c64aa200b7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33506008"
---
# <a name="uritemplate-table-dispatcher-sample"></a>Ukázka dispečera tabulky UriTemplate
<xref:System.UriTemplateTable> Třída poskytuje strukturu asociativní tabulky jako slovník pro práci s sadu <xref:System.UriTemplate> instance. Tento příklad znázorňuje modul základní odesílající vytvořená s využitím `UriTemplateTable`, běžné scénáře použití `UriTemplateTable` – třída.  
  
 Tento příklad znázorňuje následující klíčové koncepty `UriTemplateTable` třídy:  
  
-   Přidružování delegátů s `UriTemplates` v `UriTemplateTable`.  
  
-   Pomocí <xref:System.UriTemplateTable.MatchSingle%2A> získat delegát správné obslužné rutiny pro konkrétní identifikátoru URI.  
  
-   Vyvolání delegáta obslužné rutiny pro zpracování požadavku.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2.  Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\UriTemplateDispatcher`  
  
## <a name="see-also"></a>Viz také  
 [Tabulka UriTemplate](../../../../docs/framework/wcf/samples/uritemplate-table-sample.md)  
 [UriTemplate](../../../../docs/framework/wcf/samples/uritemplate-sample.md)
