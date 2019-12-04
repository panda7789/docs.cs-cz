---
title: Ukázka UriTemplate
ms.date: 03/30/2017
ms.assetid: 0aaf91d0-ce18-468d-8006-bc9bc2e48231
ms.openlocfilehash: c9dd8bdd21a075dca590c9446808860c006c18f8
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715427"
---
# <a name="uritemplate-sample"></a>Ukázka UriTemplate
Třída <xref:System.UriTemplate> poskytuje metody pro práci se sadami identifikátorů URI, které sdílejí společnou strukturu. Tato ukázka demonstruje následující klíčové koncepty týkající se `UriTemplate`:  
  
- Syntaxe pro vytváření šablon  
  
- Vytváření instancí identifikátorů URI z `UriTemplate` pomocí <xref:System.UriTemplate.BindByName%2A> a <xref:System.UriTemplate.BindByPosition%2A>.  
  
- <xref:System.UriTemplateTable.Match%2A>, což je inverzní operace `BindByName` a `BindByPosition`.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2. Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Ukázky již mohou být nainstalovány v počítači. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\UriTemplate`  
  
## <a name="see-also"></a>Viz také:

- [Tabulka UriTemplate](../../../../docs/framework/wcf/samples/uritemplate-table-sample.md)
- [Dispečer tabulky UriTemplate](../../../../docs/framework/wcf/samples/uritemplate-table-dispatcher-sample.md)
