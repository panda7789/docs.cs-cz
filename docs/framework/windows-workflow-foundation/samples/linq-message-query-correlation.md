---
title: Korelace dotazů zprávy LINQ
ms.date: 03/30/2017
ms.assetid: b746872e-57b1-4514-b337-53398a0e0deb
ms.openlocfilehash: 202d65914d32245952f308d3115ec93231f95f15
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989328"
---
# <a name="linq-message-query-correlation"></a>Korelace dotazů zprávy LINQ
Tato ukázka předvádí, jak provést korelaci založenou na obsahu <xref:System.ServiceModel.Dispatcher.MessageQuery> pomocí vlastní implementace na rozdíl od systému poskytnutého <xref:System.ServiceModel.XPathMessageQuery>systémem.  
  
## <a name="demonstrates"></a>Demonstruje  
 Vlastní <xref:System.ServiceModel.Dispatcher.MessageQuery>, korelace na základě obsahu.  
  
## <a name="discussion"></a>Účely  
 Tento příklad ukazuje, jak lze z <xref:System.ServiceModel.Dispatcher.MessageQuery> základní třídy roztáhnout pro účely korelace. Vlastní implementace `LinqMessageQuery`umožňuje uživatelům poskytnout XName k vyhledání ve zprávě pomocí XLinq. Data načtená dotazem slouží k vytvoření korelačního klíče pro odeslání zpráv do příslušné instance pracovního postupu.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Tato ukázka zveřejňuje službu pracovního postupu pomocí koncových bodů HTTP. Pokud chcete tuto ukázku spustit, musí se přidat správné seznamy ACL adresy URL (podrobnosti najdete v tématu [Konfigurace HTTP a HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353) ), a to buď spuštěním sady Visual Studio jako správce, nebo spuštěním následujícího příkazu na příkazovém řádku se zvýšenými oprávněními, abyste přidali příslušné seznamy ACL. Ujistěte se, že je nahrazena vaše doména a uživatelské jméno.  
  
    ```console  
    netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%  
    ```  
  
2. Po přidání seznamů ACL adresy URL použijte následující postup.  
  
    1. Sestavte řešení.  
  
    2. Nastavte více spouštěcích projektů kliknutím pravým tlačítkem na řešení a výběrem možnosti **nastavit projekty po spuštění**. Přidejte **službu** a **klienta** (v tomto pořadí) jako několik spouštěcích projektů.  
  
    3. Spusťte aplikaci. Konzola klienta zobrazuje pracovní postup odesílající objednávku a příjem ID nákupní objednávky a následně potvrzuje objednávku. V okně služby se zobrazí zpracovávané požadavky.  
  
> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\LinqMessageQueryCorrelation`
