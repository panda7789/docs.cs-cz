---
ms.openlocfilehash: daf09748e69e70ad982bcee14461b66579f3bb87
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614561"
---
### <a name="avoiding-endless-recursion-for-iworkflowinstancemanagementtransactedcancel-and-iworkflowinstancemanagementtransactedterminate"></a>Zamezení nekonečné rekurzování pro IWorkflowInstanceManagement. TransactedCancel a IWorkflowInstanceManagement. TransactedTerminate

#### <a name="details"></a>Podrobnosti

Za určitých okolností, kdy <xref:System.ServiceModel.Activities.IWorkflowInstanceManagement.TransactedCancel%2A?displayProperty=nameWithType> pomocí <xref:System.ServiceModel.Activities.IWorkflowInstanceManagement.TransactedTerminate%2A?displayProperty=nameWithType> rozhraní API nebo zrušení nebo ukončení instance služby worklow, může instance pracovního postupu dojít k přetečení zásobníku z důvodu nekonečné rekurze, když se `Workflow` modul runtime pokusí zachovat instanci služby v rámci zpracování žádosti. K tomuto problému dochází, pokud je instance pracovního postupu ve stavu, kdy čeká na dokončení jiné zbývající žádosti WCF na jinou službu. `TransactedCancel`Operace a `TransactedTerminate` vytvoří pracovní položky, které jsou zařazeny do fronty pro instanci služby pracovního postupu. Tyto pracovní položky nejsou provedeny jako součást zpracování `TransactedCancel/TransactedTerminate` žádosti. Vzhledem k tomu, že instance služby pracovního postupu je zaneprázdněná čekáním na dokončení jiné zbývající žádosti WCF, bude vytvořená pracovní položka zařazená do fronty. `TransactedCancel/TransactedTerminate`Operace se dokončí a ovládací prvek se vrátí zpátky na klienta. V případě, že transakce přidružená k `TransactedCancel/TransactedTerminate` operaci se pokusí o potvrzení, musí zachovat stav instance službě pracovního postupu. Ale vzhledem k tomu, že existuje nekonečný `WCF` požadavek na instanci, modul runtime pracovního postupu nemůže zachovat instanci služby pracovního postupu a nekonečné smyčka rekurze vede k přetečení zásobníku. Protože `TransactedCancel` a `TransactedTerminate` pouze vytvoří pracovní položku v paměti, fakt, že transakce existuje, nemá žádný vliv. Vrácení zpět transakce nezruší pracovní položku. Pro vyřešení tohoto problému, který začíná v .NET Framework 4.7.2, jsme představili `AppSetting` , kterou je možné přidat do `web.config/app.config` služby pracovního postupu, která mu oznamuje, že má ignorovat transakce pro `TransactedCancel` a `TransactedTerminate` . To umožňuje transakci potvrdit bez čekání na zachování instance pracovního postupu. AppSetting pro tuto funkci je pojmenována `microsoft:WorkflowServices:IgnoreTransactionsForTransactedCancelAndTransactedTerminate` . Hodnota `true` označuje, že by měla být transakce ignorována, čímž se vyhne přetečení zásobníku. Výchozí hodnota tohoto AppSetting je `false` , takže existující instance služby pracovního postupu nebudou ovlivněny.

#### <a name="suggestion"></a>Návrh

Pokud používáte AppFabric nebo jiného <xref:System.ServiceModel.Activities.IWorkflowInstanceManagement> klienta a při pokusu o zrušení nebo ukončení instance pracovního postupu dojde k přetečení zásobníku v instanci službě pracovního postupu, můžete do `<appSettings>` části souboru web.config/app.config pro službu pracovního postupu přidat následující:

<pre><code class="lang-xml">&lt;add key=&quot;microsoft:WorkflowServices:IgnoreTransactionsForTransactedCancelAndTransactedTerminate&quot; value=&quot;true&quot;/&gt;&#13;&#10;</code></pre>

Pokud se problém nevyřeší, nemusíte to dělat.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   | Edge        |
| Verze | 4.7.2       |
| Typ    | Změna cílení |
