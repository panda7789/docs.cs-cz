---
title: Ukázka UriTemplate
ms.date: 03/30/2017
ms.assetid: 0aaf91d0-ce18-468d-8006-bc9bc2e48231
ms.openlocfilehash: 15799c1aaf3ed7df5f7721368dea426665dcf335
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044601"
---
# <a name="uritemplate-sample"></a>Ukázka UriTemplate
<xref:System.UriTemplate> Třída poskytuje metody pro práci se sadami identifikátorů URI, které sdílejí společnou strukturu. Tato ukázka demonstruje následující klíčové koncepty týkající `UriTemplate`se:  
  
- Syntaxe pro vytváření šablon  
  
- Vytváření instancí identifikátorů URI `UriTemplate` z <xref:System.UriTemplate.BindByName%2A> pomocí <xref:System.UriTemplate.BindByPosition%2A>a.  
  
- <xref:System.UriTemplateTable.Match%2A>, což je inverzní operace `BindByName` a. `BindByPosition`  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu sestavování [ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2. Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Ukázky již mohou být nainstalovány v počítači. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\UriTemplate`  
  
## <a name="see-also"></a>Viz také:

- [Tabulka UriTemplate](../../../../docs/framework/wcf/samples/uritemplate-table-sample.md)
- [Dispečer tabulky UriTemplate](../../../../docs/framework/wcf/samples/uritemplate-table-dispatcher-sample.md)
