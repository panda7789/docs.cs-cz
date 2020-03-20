---
title: Korelace dotazů zprávy LINQ
ms.date: 03/30/2017
ms.assetid: b746872e-57b1-4514-b337-53398a0e0deb
ms.openlocfilehash: 507001b165efdcbe7c1e27a07749dbe2eafb468f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182808"
---
# <a name="linq-message-query-correlation"></a>Korelace dotazů zprávy LINQ
Tato ukázka ukazuje, jak provést korelaci <xref:System.ServiceModel.Dispatcher.MessageQuery> založenou na obsahu pomocí <xref:System.ServiceModel.XPathMessageQuery>vlastní implementace na rozdíl od poskytovaného systému .  
  
## <a name="demonstrates"></a>Demonstruje  
 Vlastní <xref:System.ServiceModel.Dispatcher.MessageQuery>korelace založená na obsahu.  
  
## <a name="discussion"></a>Diskuse  
 Tato ukázka ukazuje, <xref:System.ServiceModel.Dispatcher.MessageQuery> jak rozšířit ze základní třídy pro účely korelace. Vlastní implementace `LinqMessageQuery`, umožňuje uživatelům poskytnout XName najít ve zprávě pomocí XLinq. Data načtená dotazem se používají k vytvoření klíče korelace pro odeslání zpráv do příslušné instance pracovního postupu.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Tato ukázka zveřejňuje službu pracovního postupu pomocí koncových bodů HTTP. Chcete-li spustit tuto ukázku, musí být přidány správné adresy ACL správné adresy URL (viz [Konfigurace protokolu HTTP a HTTPS](../../wcf/feature-details/configuring-http-and-https.md) podrobnosti), buď spuštěním sady Visual Studio jako správce, nebo spuštěním následujícího příkazu ve zvýšené výzvě k přidání příslušných seznamu ACL. Ujistěte se, že vaše doména a uživatelské jméno jsou nahrazeny.  
  
    ```console  
    netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%  
    ```  
  
2. Po přidání adres URL aklů použijte následující kroky.  
  
    1. Sestavte řešení.  
  
    2. Nastavte více počátečních projektů klepnutím pravým tlačítkem myši na řešení a výběrem **možnosti Nastavit projekty po spuštění**. Přidejte **službu** a **klienta** (v tomto pořadí) jako více start-up projektů.  
  
    3. Spusťte aplikaci. Klientská konzola zobrazuje pracovní postup, který odesílá objednávku a přijímá ID nákupní objednávky a následně objednávku potvrzuje. Okno Služba zobrazí zpracovávané požadavky.  
  
> [!IMPORTANT]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\LinqMessageQueryCorrelation`
