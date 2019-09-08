---
title: Tok zpráv – přehled
ms.date: 03/30/2017
ms.assetid: fb0899e1-84cc-4d90-b45b-dc5a50063943
ms.openlocfilehash: 0bfbd1523f1d5db4a94cf3af03a03779af14655d
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795967"
---
# <a name="message-flow-overview"></a>Tok zpráv – přehled
V distribuovaném systému, který obsahuje propojené služby, je nutné určit příčinné vztahy mezi službami. Je důležité pochopit různé komponenty, které byly součástí toku požadavků pro podporu kritických scénářů, jako je monitorování stavu, odstraňování potíží a analýza hlavní příčiny. Pokud chcete povolit korelaci trasování mezi různými službami, v .NET Framework 4 jsme přidali podporu prostřednictvím následujících funkcí:

- Analytické trasování: Funkce pro sledování vysokého výkonu a nízké podrobností pomocí trasování událostí pro Windows (ETW).

- Koncový model aktivit pro služby WCF/WF: Tato funkce podporuje korelaci trasování vygenerovaných <xref:System.ServiceModel> obory názvů a <xref:System.Workflow.ComponentModel> .

- Sledování ETW pro WF: Tato funkce používá sledování záznamů generovaných službami WF k zajištění viditelnosti aktuálního stavu a průběhu pracovního postupu.

 Chyby zaznamenané v záznamu sledování nebo trasování lze použít k vyhledání vad kódu nebo nesprávně vytvořených zpráv. K určení aktivity selhání lze použít vlastnost ActivityId uzlu korelace v hlavičce zprávy události. Postup povolení trasování toku zpráv podle ID aktivity najdete v tématu [Konfigurace trasování toku zpráv](./etw/configuring-message-flow-tracing.md). Toto téma ukazuje, jak povolit trasování toku zpráv v projektu vytvořeném v Začínámem kurzu.

### <a name="to-enable-message-flow-tracing-in-the-getting-started-tutorial"></a>Postup povolení trasování toku zpráv v Začínáme kurzu

1. Otevřete Prohlížeč událostí kliknutím na **Start**, **Spustit**a zadáním `eventvwr.exe`.

2. Pokud jste nepovolili analytické trasování, rozbalte **protokoly aplikací a služeb**, **Microsoft**, **Windows**, **aplikační server – aplikace**. Vyberte **zobrazení**, **Zobrazte protokoly o ladění a ladění**. Klikněte pravým tlačítkem na možnost **analytické** a vyberte **Povolit protokol**. Nechejte Prohlížeč událostí otevřené, aby bylo možné zobrazit trasování.

3. Otevřete ukázku vytvořenou v [Začínáme kurzu](../getting-started-tutorial.md) v aplikaci Visual Studio 2012. Všimněte si, že je nutné spustit aplikaci Visual Studio 2012 jako správce, aby bylo možné službu vytvořit. Pokud máte nainstalované ukázky WCF, můžete otevřít [Začínáme](../samples/getting-started-sample.md), který obsahuje dokončený projekt vytvořený v tomto kurzu.

4. Klikněte pravým tlačítkem na projekt **služby** a vyberte **Přidat**, **Nová položka**. Vyberte **konfigurační soubor aplikace** a klikněte na **OK**.

5. Do souboru App. config, který jste vytvořili v předchozím kroku, přidejte následující kód.

    ```xml
    <system.serviceModel>
      <diagnostics>
        <endToEndTracing propagateActivity="true" messageFlowTracing="true"/>
      </diagnostics>
    </system.serviceModel>
    ```

6. Spusťte aplikaci serveru bez ladění stisknutím kombinace kláves CTRL + F5. Spusťte projekt klienta kliknutím pravým tlačítkem myši na projekt **klienta** a výběrem možnosti **ladění**, **spustit novou instanci**.

7. Chcete-li trasovat události z klienta na server, přidejte následující do konfiguračního souboru aplikace v klientském projektu.

    ```xml
    <diagnostics>
      <endToEndTracing propagateActivity="true" messageFlowTracing="true"/>
    </diagnostics>
    ```

8. V Program.cs v klientovi přidejte následující příkaz using.

    ```csharp
    using System.Diagnostics;
    ```

9. V metodě Main v souboru program.cs v projektu klienta nastavte identifikátor GUID trasování, který se má rozšířit do protokolu událostí.

    ```csharp
    Guid guid = Guid.NewGuid();
    Trace.CorrelationManager.ActivityId = guid;
    ```

10. Aktualizujte a Projděte si **analytický** protokol.  Vyhledejte událost s ID události 220.  Vyberte událost a klikněte na kartu **Podrobnosti** v podokně náhledu. Tato událost bude obsahovat ID korelace pro volající aktivitu.

    ```xml
    <Correlation ActivityID="{A066CCF1-8AB3-459B-B62F-F79F957A5036}" />
    ```

    > [!NOTE]
    > Všechny události se stejným identifikátorem GUID v ActivityID souvisejí s jednou žádostí. Dá se použít ke korelaci zpráv od určitého klienta ke konkrétní službě. Pokud klient volal jinou službu, může být stejný klient identifikován nástrojem ActivityID.

11. V některých případech se ActivityID může změnit z původního GUID na nový ActivityID. V takovém případě je vyvolána událost přenosu. ID události je 499 a v hlavičce bude událost obsahovat následující data.

    ```xml
    <Event xmlns="http://schemas.microsoft.com/win/2004/08/events/event">
        <System>
            <Provider Name="Microsoft-Windows-Application Server-Applications" Guid="{c651f5f6-1c0d-492e-8ae1-b4efd7c9d503}" />
            <EventID>499</EventID>
            ...
            <Correlation ActivityID="{A066CCF1-8AB3-459B-B62F-F79F957A5036}" RelatedActivityID="{85FC0930-9C49-42DA-804B-A7368104BD1B}" />
            ...
       </System>
    </Event>
    ```

    > [!NOTE]
    > Událost přenosu zaznamenává změnu aktivního ActivityID z identifikátoru GUID zadaného jako ActivityID k identifikátoru GUID, který je zadaný jako objekt. Po vygenerování události přenosu budou všechny události obsahovat nový identifikátor GUID jako ActivityID.
