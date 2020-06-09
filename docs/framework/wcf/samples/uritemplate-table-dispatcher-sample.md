---
title: Ukázka dispečera tabulky UriTemplate
ms.date: 03/30/2017
ms.assetid: 3b32975d-ba90-4c5c-83bc-2fbb48f11c0c
ms.openlocfilehash: 97e916aaf9d137eb7931470f9565797b03620d28
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84591069"
---
# <a name="uritemplate-table-dispatcher-sample"></a>Ukázka dispečera tabulky UriTemplate
<xref:System.UriTemplateTable>Třída poskytuje tabulkovou strukturu asociativní tabulky pro práci se sadou <xref:System.UriTemplate> instancí. Tato ukázka předvádí základní modul pro expedici sestavený pomocí `UriTemplateTable` , společný scénář použití pro `UriTemplateTable` třídu.  
  
 Tato ukázka demonstruje následující klíčové koncepty pro `UriTemplateTable` třídu:  
  
- Přidružení delegátů k `UriTemplates` v `UriTemplateTable` .  
  
- Použijte <xref:System.UriTemplateTable.MatchSingle%2A> k získání správného delegáta obslužné rutiny pro konkrétní identifikátor URI.  
  
- Volání delegáta obslužné rutiny pro zpracování žádosti.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Chcete-li sestavit edici C# nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](building-the-samples.md).  
  
2. Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](running-the-samples.md).  
  
> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\UriTemplateDispatcher`  
  
## <a name="see-also"></a>Viz také

- [Tabulka UriTemplate](uritemplate-table-sample.md)
- [UriTemplate](uritemplate-sample.md)
