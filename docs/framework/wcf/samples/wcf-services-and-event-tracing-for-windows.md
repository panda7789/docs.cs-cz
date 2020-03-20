---
title: Služby WCF a Trasování událostí pro Windows
ms.date: 03/30/2017
ms.assetid: eda4355d-0bd0-4dc9-80a2-d2c832152272
ms.openlocfilehash: b8a1f30f20aa2c541a574a070b3644569d633ca2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183202"
---
# <a name="wcf-services-and-event-tracing-for-windows"></a>Služby WCF a Trasování událostí pro Windows
Tato ukázka ukazuje, jak použít analytické trasování v Systému Windows Communication Foundation (WCF) k vyzařování událostí v trasování událostí pro Windows (ETW). Analytické trasování jsou události vyzařované v klíčových bodech v zásobníku WCF, které umožňují řešení potíží se službami WCF v produkčním prostředí.

 Analytické trasování ve službách WCF je trasování, které lze zapnout v produkčním prostředí s minimálním dopadem na výkon. Tyto trasování jsou vydávány jako události relace ETW.

 Tato ukázka zahrnuje základní službu WCF, ve které jsou události vyzařovány ze služby do protokolu událostí, které lze zobrazit pomocí Prohlížeče událostí. Je také možné spustit vyhrazené relace ETW, který naslouchá události ze služby WCF. Ukázka obsahuje skript pro vytvoření vyhrazené relace ETW, která ukládá události v binárním souboru, který lze číst pomocí Prohlížeče událostí.

#### <a name="to-use-this-sample"></a>Chcete-li použít tento vzorek

1. Pomocí Visual Studia 2012 otevřete soubor řešení EtwAnalyticTraceSample.sln.

2. Chcete-li vytvořit řešení, stiskněte kombinaci kláves CTRL+SHIFT+B.

3. Chcete-li řešení spustit, stiskněte kombinaci kláves CTRL+F5.

     Ve webovém prohlížeči klepněte na položku **Calculator.svc**. Identifikátor URI dokumentu WSDL pro službu by se měl zobrazit v prohlížeči. Zkopírujte tento identifikátor URI.

     Ve výchozím nastavení služba spustí naslouchání požadavkům `http://localhost:1378/Calculator.svc`na portu 1378 .

4. Spusťte testovacího klienta WCF (WcfTestClient.exe).

     Testovací klient WCF (WcfTestClient.exe) `\<Visual Studio 2012 Install Dir>\Common7\IDE\WcfTestClient.exe`je umístěn na adrese .  Výchozí instalační dir sady Visual Studio `C:\Program Files\Microsoft Visual Studio 10.0`2012 je .

5. V rámci testovacího klienta WCF přidejte službu výběrem **položky Soubor**a potom **přidejte službu**.

     Přidejte adresu koncového bodu do vstupního pole. Výchozí formát je `http://localhost:1378/Calculator.svc`.

6. Otevřete aplikaci Prohlížeč událostí.

     Před vyvoláním služby spusťte Prohlížeč událostí a ujistěte se, že protokol událostí naslouchá sledování událostí vyzařovaných ze služby WCF.

7. V nabídce **Start** vyberte **Nástroje pro správu**a potom **prohlížeč událostí**.  Povolte protokoly **Analytic a** **Ladění.**

8. Ve stromovém zobrazení v Prohlížeči událostí přejděte do **prohlížeče událostí**, **protokoly aplikací a služeb**, **Microsoft**, **Windows**a potom na **aplikace aplikačního serveru**. Klepněte pravým tlačítkem myši na **položku Aplikační server-Aplikace**, vyberte příkaz **Zobrazit**a potom **zobrazit protokoly analýzy a ladění**.

     Ujistěte se, že je zaškrtnuta možnost **Zobrazit protokoly analýzy a ladění.**

9. Povolte protokol **Analytická.**

     Ve stromovém zobrazení v Prohlížeči událostí přejděte do **prohlížeče událostí**, **protokoly aplikací a služeb**, **Microsoft**, **Windows**a potom na **aplikace aplikačního serveru**. Klepněte pravým tlačítkem myši na **službu Analytick** a vyberte **příkaz Povolit protokol**.

#### <a name="to-test-the-service"></a>Chcete-li otestovat službu

1. Přepněte zpět do testovacího klienta WCF a poklepejte na `Divide` výchozí hodnoty, které určují jmenovatel 0.

     Pokud je jmenovatel 0, pak služba vyvolá chybu.

2. Sledujte události vyzařované ze služby.

     Přepněte zpět do Prohlížeče událostí a přejděte do **prohlížeče událostí**, **protokolů aplikací a služeb**, společnosti **Microsoft**, **Systému Windows**a **následných aplikací aplikačního serveru**. Klikněte pravým tlačítkem myši na **Službu Analyticka** a vyberte **aktualizovat**.

     V prohlížeči událostí jsou zobrazeny události analytického trasování WCF. Všimněte si, že vzhledem k tomu, že služba vyvolala chybu, zobrazí se v prohlížeči událostí událost sledování chyb.

3. Opakujte kroky 1 a 2, ale s platnými vstupy. Hodnota parametru `N2` může být libovolné číslo než 0.

     Aktualizujte analytický kanál pro zobrazení událostí WCF neobsahují žádné chybové události.

 Ukázka ukazuje události trasování analytická vyzařované ze služby WCF.

#### <a name="to-cleanup-optional"></a>Vyčištění (volitelné)

1. Otevřete Prohlížeč událostí.

2. Přejděte do **prohlížeče událostí**, **protokolů aplikací a služeb**, společnosti **Microsoft**, **Systému Windows**a **následných aplikací aplikačního serveru**. Klepněte pravým tlačítkem myši na **službu Analytická** a vyberte **příkaz Zakázat protokol**.

3. Přejděte do **prohlížeče událostí**, **protokolů aplikací a služeb**, společnosti **Microsoft**, **Systému Windows**a **následných aplikací aplikačního serveru**. Klepněte pravým tlačítkem myši na **položku Analytická** a vyberte příkaz **Vymazat protokol**.

4. Zvolte možnost **Vymazat,** chcete-li události vymazat.

> [!IMPORTANT]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ETWTracing`  
  
## <a name="see-also"></a>Viz také

- [Vzorky monitorování appfabricu](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))
