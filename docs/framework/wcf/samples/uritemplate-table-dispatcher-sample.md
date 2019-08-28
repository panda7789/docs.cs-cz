---
title: Ukázka dispečera tabulky UriTemplate
ms.date: 03/30/2017
ms.assetid: 3b32975d-ba90-4c5c-83bc-2fbb48f11c0c
ms.openlocfilehash: 724a13504cea2672aef7ff155fbbff055aac34e6
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044580"
---
# <a name="uritemplate-table-dispatcher-sample"></a>Ukázka dispečera tabulky UriTemplate
Třída poskytuje tabulkovou strukturu asociativní tabulky pro práci se <xref:System.UriTemplate> sadou instancí. <xref:System.UriTemplateTable> Tato ukázka předvádí základní modul pro expedici sestavený `UriTemplateTable`pomocí, společný scénář použití `UriTemplateTable` pro třídu.  
  
 Tato ukázka demonstruje následující klíčové koncepty pro `UriTemplateTable` třídu:  
  
- Přidružení delegátů k `UriTemplates` `UriTemplateTable`v.  
  
- Použijte <xref:System.UriTemplateTable.MatchSingle%2A> k získání správného delegáta obslužné rutiny pro konkrétní identifikátor URI.  
  
- Volání delegáta obslužné rutiny pro zpracování žádosti.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu sestavování [ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2. Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\UriTemplateDispatcher`  
  
## <a name="see-also"></a>Viz také:

- [Tabulka UriTemplate](../../../../docs/framework/wcf/samples/uritemplate-table-sample.md)
- [UriTemplate](../../../../docs/framework/wcf/samples/uritemplate-sample.md)
