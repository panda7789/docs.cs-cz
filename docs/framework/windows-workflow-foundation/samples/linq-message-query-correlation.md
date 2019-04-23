---
title: Korelace dotazů zprávy LINQ
ms.date: 03/30/2017
ms.assetid: b746872e-57b1-4514-b337-53398a0e0deb
ms.openlocfilehash: cc13696cfd8eb2dcdf22fdc067518c8bd55ca32d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2019
ms.locfileid: "59973314"
---
# <a name="linq-message-query-correlation"></a>Korelace dotazů zprávy LINQ
Tato ukázka předvádí, jak provádět korelace na základě obsahu pomocí vlastní <xref:System.ServiceModel.Dispatcher.MessageQuery> implementace na rozdíl od poskytnuté systémem <xref:System.ServiceModel.XPathMessageQuery>.  
  
## <a name="demonstrates"></a>Demonstruje  
 Vlastní <xref:System.ServiceModel.Dispatcher.MessageQuery>, korelace na základě obsahu.  
  
## <a name="discussion"></a>Diskuse  
 Tento příklad ukazuje, jak rozšířit z <xref:System.ServiceModel.Dispatcher.MessageQuery> základní třída pro účely korelace. Vlastní implementace `LinqMessageQuery`, umožňuje uživatelům poskytnout XName najít ve zprávě pomocí XLinq. Data načtená dotazem slouží k tvoří klíč korelace k odeslání zprávy do instance odpovídající pracovního postupu.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1. Tato ukázka poskytuje služby pracovního postupu pomocí koncových bodů HTTP. Chcete-li spustit ukázku, správné seznamy ACL adresa URL musí být přidán (naleznete v tématu [konfigurace HTTP a HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353) podrobnosti), buď pomocí sady Visual Studio jako správce nebo spuštěním následujícího příkazu na řádku se zvýšenými oprávněními přidejte příslušné seznamy ACL. Ujistěte se, že jsou nahrazeny doména a uživatelské jméno.  
  
    ```  
    netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%  
    ```  
  
2. Po přidání se seznamy ACL adresu URL, pomocí následujícího postupu.  
  
    1.  Sestavte řešení.  
  
    2.  Nastavení více projektů spuštění tak, že kliknete pravým tlačítkem řešení a vyberete **nastavit projekty po spuštění**. Přidat **služby** a **klienta** (v uvedeném pořadí) jako více spuštění projektů.  
  
    3.  Spusťte aplikaci. Klientské konzoly zobrazuje pracovní postup odeslání objednávky a přijímá id nákupní objednávky a následně potvrzení objednávky. V okně služby zobrazí zpracovávaných žádostí.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\LinqMessageQueryCorrelation`
