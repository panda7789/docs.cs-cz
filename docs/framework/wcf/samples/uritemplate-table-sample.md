---
title: Ukázková tabulka UriTemplate
ms.date: 03/30/2017
ms.assetid: 5dd1d38f-1989-4c64-820d-821f5a02216a
ms.openlocfilehash: ff88bdfe0c8c32da6f07f2b22de54af437376c51
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596432"
---
# <a name="uritemplate-table-sample"></a>Ukázková tabulka UriTemplate
<xref:System.UriTemplateTable>Třída poskytuje tabulkovou strukturu asociativní tabulky pro práci se sadou `UriTemplate` instancí. Konkrétní identifikátory URI (Uniform Resource Identifier) lze efektivně porovnat proti všem šablonám v tabulce a data přidružená k odpovídající šabloně lze načíst.  
  
 Tato ukázka demonstruje následující klíčové koncepty týkající se `UriTemplateTable` třídy:  
  
- Syntaxe pro vytvoření instance `UriTemplateTable` .  
  
- Naplnění `UriTemplateTable` se sadou párů klíč/hodnota.  
  
- Odpovídá kandidátu identifikátoru URI na tabulku pomocí <xref:System.UriTemplateTable.MatchSingle%2A> .  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Chcete-li sestavit edici C# nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](building-the-samples.md).  
  
2. Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](running-the-samples.md).  
  
> [!IMPORTANT]
> Ukázky již mohou být nainstalovány v počítači. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\UriTemplateTable`  
  
## <a name="see-also"></a>Viz také

- [Dispečer tabulky UriTemplate](uritemplate-table-dispatcher-sample.md)
- [UriTemplate](uritemplate-sample.md)
