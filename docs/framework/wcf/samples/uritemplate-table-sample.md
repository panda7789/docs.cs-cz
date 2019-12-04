---
title: Ukázková tabulka UriTemplate
ms.date: 03/30/2017
ms.assetid: 5dd1d38f-1989-4c64-820d-821f5a02216a
ms.openlocfilehash: fb5932acce60e2da45f99730580237d31130d918
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715404"
---
# <a name="uritemplate-table-sample"></a>Ukázková tabulka UriTemplate
Třída <xref:System.UriTemplateTable> poskytuje pro práci se sadou instancí `UriTemplate` asociativní strukturu tabulkového typu. Konkrétní identifikátory URI (Uniform Resource Identifier) lze efektivně porovnat proti všem šablonám v tabulce a data přidružená k odpovídající šabloně lze načíst.  
  
 Tato ukázka demonstruje následující klíčové koncepty související s `UriTemplateTable` třídou:  
  
- Syntaxe pro vytvoření instance `UriTemplateTable`.  
  
- Naplnění `UriTemplateTable` se sadou párů klíč/hodnota.  
  
- Porovnání kandidátu identifikátoru URI s tabulkou pomocí <xref:System.UriTemplateTable.MatchSingle%2A>.  
  
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
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\UriTemplateTable`  
  
## <a name="see-also"></a>Viz také:

- [Dispečer tabulky UriTemplate](../../../../docs/framework/wcf/samples/uritemplate-table-dispatcher-sample.md)
- [UriTemplate](../../../../docs/framework/wcf/samples/uritemplate-sample.md)
