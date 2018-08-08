---
title: 'Postupy: Vytvoření klienta Windows Communication Foundation'
ms.date: 03/30/2017
helpviewer_keywords:
- clients [WCF], running
- WCF clients [WCF], running
ms.assetid: a67884cc-1c4b-416b-8c96-5c954099f19f
ms.openlocfilehash: d2932293536f875d8986d8d49842cddc196ced0f
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33806270"
---
# <a name="how-to-create-a-windows-communication-foundation-client"></a>Postupy: Vytvoření klienta Windows Communication Foundation
Toto je čtvrtý šesti úlohy, které jsou potřebné pro vytvoření aplikace Windows Communication Foundation (WCF). Přehled všech šest úloh najdete v tématu [kurzu Začínáme](../../../docs/framework/wcf/getting-started-tutorial.md) tématu.  
  
 Toto téma popisuje, jak načíst metadata ze služby WCF a použít ji k vytvoření WCF proxy server, který mají přístup ke službě. Tato úloha je dokončit pomocí funkce Přidat odkaz na službu poskytované sadě Visual Studio. Tento nástroj získává metadata z koncového bodu služby MEX a vygeneruje soubor spravované zdrojového kódu pro proxy server na klienta v jazyce zvolili jste (C# ve výchozím nastavení). Kromě vytváření proxy serveru klienta, nástroj také vytvoří nebo aktualizuje klienta konfigurační soubor, který umožňuje aplikaci připojit ke službě v některém z jeho koncových bodů klienta.  
  
> [!NOTE]
>  Můžete také [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) nástroj pro generování třídy proxy serveru a konfigurace místo použití přidat odkaz na službu v aplikaci Visual Studio.  
  
> [!WARNING]
>  Při volání služby WCF z projektu knihovny tříd v [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] můžete použít funkci Přidat odkaz na službu k automatickému generování proxy a přidružené konfigurační soubor.  Konfigurační soubor se nepoužijí projektu knihovny tříd. Musíte přidat nastavení v generované konfiguračního souboru do souboru app.config pro spustitelný soubor, který bude volat knihovny tříd.  
  
 Klientská aplikace používá třídu vygenerovaný proxy server pro komunikaci se službou. Tento postup je popsaný v [postupy: používání klienta](../../../docs/framework/wcf/how-to-use-a-wcf-client.md).  
  
### <a name="to-create-a-windows-communication-foundation-client"></a>Vytvoření klienta Windows Communication Foundation  
  
1.  Vytvořit nový projekt konzolové aplikace kliknutím pravým tlačítkem na řešení Začínáme vyberete, **přidat**, **nový projekt**. V **přidat nový projekt** dialog v dialogovém okně vyberte na levé straně **Windows** pod **C#** nebo **VB**. V části center dialogového okna Vybrat **konzolové aplikace**. Název projektu `GettingStartedClient`.  
  
2.  Nastavte cílový framework projektu GettingStartedClient na rozhraní .NET Framework 4.5 kliknutím pravým tlačítkem na **GettingStartedClient** v Průzkumníku řešení a výběrem **vlastnosti**. Rozevírací pole s popiskem **cílové rozhraní** vyberte **rozhraní .NET Framework 4.5**. Nastavení cílové rozhraní projektu jazyka Visual Basic je mírně liší v dialogovém okně Vlastnosti projektu GettingStartedClient, klikněte na tlačítko **zkompilovat** na levé straně obrazovky a pak klikněte **Upřesnit Kompilace možnosti** tlačítko v levém dolním rohu dialogu. Potom vyberte **rozhraní .NET Framework 4.5** rozevírací pole s popiskem **cílové rozhraní**.  
  
     Nastavení rozhraní target framework způsobí sady Visual Studio 2011 znovu načíst řešení, stiskněte klávesu **OK** po zobrazení výzvy.  
  
3.  Přidat odkaz na System.ServiceModel do projektu GettingStartedClient kliknutím pravým tlačítkem myši **odkaz** ve složce projektu GettingStartedClient v Průzkumníku řešení a vyberte **přidat** Odkaz. V **přidat odkaz na** dialogovém okně vyberte **Framework** na levé straně dialogového okna. Zadejte do textového pole hledání sestavení v `System.ServiceModel`. V části center dialogového okna Vybrat **System.ServiceModel**, klikněte na tlačítko **přidat** tlačítko a klikněte na tlačítko **Zavřít** tlačítko. Uložte řešení klepnutím **Uložit vše** tlačítko níže v hlavní nabídce.  
  
4.  Další wlll přidat odkaz na službu ve službě kalkulačky. Předtím, než můžete to udělat, musíte spustit až GettingStartedHost konzolové aplikace. Jakmile je na hostiteli spuštěn můžete klikněte pravým tlačítkem na složku odkazy v části GettingStartedClient projekt v Průzkumníku řešení a vyberte Přidat odkaz na službu a zadejte následující adresu URL do pole Adresa dialogového okna Přidat odkaz na službu: HYPERLINK "http://localhost:8000/ServiceModelSamples/Service" http://localhost:8000/ServiceModelSamples/Service a klikněte na **přejděte** tlačítko. CalculatorService by pak zobrazí v seznamu služeb, klikněte na dvojitou hodnotu CalculatorService a bude rozbalit a zobrazit kontraktů služby implementované službu. Ponechte výchozí obor názvů a klikněte na **OK** tlačítko.  
  
     Když přidáte, odkaz na službu pomocí sady Visual Studio nové položky se zobrazí v Průzkumníku řešení ve složce odkazů na služby v rámci GettingStartedClient projektu.  Pokud použijete [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) nástroj souboru zdrojového kódu a soubor app.config se budou generovat.  
  
     Můžete také použít nástroj příkazového řádku [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) s příslušné přepínače k vytvoření kódu klienta. Následující příklad vytvoří soubor kódu a konfigurační soubor pro službu. První příklad ukazuje, jak vygenerovat proxy serveru v jazyce Visual Basic a druhá ukazuje, jak vytvořit proxy server v jazyce C#:  
  
    ```  
    svcutil.exe /language:vb /out:generatedProxy.vb /config:app.config http://localhost:8000/ServiceModelSamples/service  
    ```  
  
    ```csharp  
    svcutil.exe /language:cs /out:generatedProxy.cs /config:app.config http://localhost:8000/ServiceModelSamples/service  
    ```  
  
 Nyní jste vytvořili proxy server, který klientská aplikace bude používat pro volání služby kalkulačky. Pokračovat na další téma v řadě: [postupy: Konfigurace klienta](../../../docs/framework/wcf/how-to-configure-a-basic-wcf-client.md)  
  
## <a name="see-also"></a>Viz také  
 [Nástroj metadat modelu služby (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)  
 [Začínáme](../../../docs/framework/wcf/samples/getting-started-sample.md)  
 [Vlastní hostování](../../../docs/framework/wcf/samples/self-host.md)  
 [Postupy: Publikování metadat služby promocí konfiguračního souboru](../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 [Postupy: Stažení dokumentů metadat pomocí nástroje Svcutil.exe](../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-download-metadata-documents.md)
