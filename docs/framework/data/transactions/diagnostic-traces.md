---
title: Diagnostická trasování
ms.date: 03/30/2017
ms.assetid: 28e77a63-d20d-4b6a-9caf-ddad86550427
ms.openlocfilehash: 56f79fb9140785188996cc413eca4dd530037ccd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61934794"
---
# <a name="diagnostic-traces"></a>Diagnostická trasování
Trasování jsou publikování určitých zpráv, které jsou generovány během spuštění aplikace. Při použití trasování, musí mít mechanismus pro shromažďování a zaznamenávání zpráv, které jsou odeslány. Trasovací zprávy jsou přijímány naslouchací procesy. Účelem tohoto naslouchací proces je shromažďování, ukládání a směrovat trasovací zprávy. Posluchači přímý výstup trasování příslušný cíli, jako je protokol, okno nebo textový soubor.  
  
 Jeden takový naslouchací proces <xref:System.Diagnostics.DefaultTraceListener>, je automaticky vytvořen a inicializován při zapnutém trasování. Pokud chcete výstup trasování k přesměrováni na jakékoli další zdroje, musíte vytvořit a inicializovat naslouchací procesy další trasování. Naslouchací procesy, které vytvoříte by měla odpovídat vašim potřebám. Například můžete text záznam všech výstupu trasování. V takovém případě by vytvořit naslouchací proces, který bylo zapsáno veškerá výstupní data do nového textového souboru, pokud povolena. Na druhé straně může být pouze chcete zobrazit výstup při spuštění aplikace. V takovém případě můžete vytvořit naslouchací proces, který řízené všechny výstup do okna konzoly. <xref:System.Diagnostics.EventLogTraceListener> Může směrovat výstup trasování do protokolu událostí a <xref:System.Diagnostics.TextWriterTraceListener> může zapisovat výstup trasování do datového proudu.  
  
## <a name="enabling-tracing"></a>Povolení trasování  
 Chcete-li povolit trasování během zpracování transakcí, měli byste upravit konfigurační soubor vaší aplikace. Následuje příklad.  
  
```xml  
<configuration>  
<system.diagnostics>  
     <sources>  
          <source name="System.Transactions" switchValue="Warning">  
               <listeners>  
                    <add name="tx"   
                     type="System.Diagnostics.XmlWriterTraceListener"   
                     initializeData= "tx.log" />  
               </listeners>  
          </source>  
     </sources>  
</system.diagnostics>  
</configuration>  
```  
  
 <xref:System.Transactions> trasování jsou zapsány do zdroje s názvem "System.Transactions". Můžete použít `add` Chcete-li určit název a typ naslouchací proces trasování, kterou chcete použít. V konfiguraci našeho příkladu jsme s názvem "tx" naslouchací proces a přidat standardní naslouchací proces trasování rozhraní .NET Framework (<xref:System.Diagnostics.XmlWriterTraceListener>) jako typ chceme použít. Použití `initializeData` nastavit název souboru protokolu pro tuto naslouchací proces. Kromě toho můžete nahradit úplná cesta k souboru jednoduchý název.  
  
 Každý typ zprávy trasování je přiřazena úroveň označuje její stupeň závažnosti. Úroveň trasování app domény je rovna nebo nižší než úroveň typu události, je vygenerována tuto zprávu. Úroveň trasování řídí `switchValue` nastavení v konfiguračním souboru. Úrovně, které jsou přidruženy k diagnostiky trasovací zprávy jsou definovány v následující tabulce.  
  
|Úroveň trasování|Popis|  
|-----------------|-----------------|  
|Kritická|Došlo k závažné chyby, jako je následující:<br /><br /> -Chybu, která může způsobit okamžité ztrátu v uživatelské funkce.<br />-Událost, která musí správce akci, aby nedošlo ke ztrátě funkčnosti.<br />– Kód přestane reagovat.<br />-Tuto úroveň trasování může také poskytnout dostatek kontext k interpretaci dalších důležitých trasování. To vám mohou pomoci identifikovat sekvence operací, což vedlo k závažné chybě.|  
|Chyba|Došlo k chybě (například neplatná konfigurace nebo v síti chování) může vést ke ztrátě funkčnosti uživatele.|  
|Upozornění|Existuje podmínka, který lze následně vést k chybě nebo kritické chyby (například přidělení nedaří nebo blíží k omezení). Normální zpracování chyb z uživatelského kódu (například transakce byla přerušena, časové limity, ověření se nezdařilo) můžete také generovat upozornění.|  
|Informace o|Zprávy, které jsou užitečné pro sledování a diagnostiku stavu systému, měření výkonu nebo profilování jsou generovány. Ty mohou zahrnovat transakce a zařazení životnost události, například transakcí vytváření nebo potvrzené překračování významné hranice nebo přidělování významných zdrojů. Vývojáři mohou využít pak tyto informace pro správu výkon a plánování kapacity.|  
  
## <a name="trace-codes"></a>Trasovací kódy  
 V následující tabulce jsou uvedeny kódy trasování, které jsou generovány <xref:System.Transactions> infrastruktury. Jsou zahrnuty v tabulce Kód identifikátor trasování <xref:System.Diagnostics.EventTypeFilter.EventType%2A> výčet úrovní trasování a doplňující data obsažená v **TraceRecord** pro trasování. Kromě toho je také uložena odpovídající úroveň trasování pro trasování v **TraceRecord**.  
  
|TraceCode|Typ události|Doplňující data v TraceRecord|  
|---------------|---------------|-------------------------------|  
|TransactionCreated|Informace o|TransactionTraceId|  
|TransactionPromoted|Informace o|Místní TransactionTraceId distribuované TransactionTraceId|  
|EnlistmentCreated|Informace o|TransactionTraceId, EnlistmentTraceId, EnlistmentType (spotřeby volatile), EnlistmentOptions|  
|EnlistmentCallbackNegative|Upozornění|TransactionTraceId, EnlistmentTraceId,<br /><br /> Zpětné volání (forcerollback/bylo přerušeno/indoubt)|  
|TransactionRollbackCalled|Upozornění|TransactionTraceId|  
|TransactionAborted|Upozornění|TransactionTraceId|  
|TransactionInDoubt|Upozornění|TransactionTraceId|  
|TransactionScopeCreated|Informace o|TransactionScopeResult, což může být následující:<br /><br /> -Novou transakci.<br />-Transakce předána.<br />-Závislé transakce předána.<br />-Pomocí aktuální transakce.<br />-Žádné transakce.<br /><br /> nové aktuální TransactionTraceId|  
|TransactionScopeDisposed|Informace o|Transactiontraceid jako obor "očekáván" aktuální transakce.|  
|TransactionScopeIncomplete|Upozornění|Transactiontraceid jako obor "očekáván" aktuální transakce.|  
|TransactionScopeNestedIncorrectly|Upozornění|Transactiontraceid jako obor "očekáván" aktuální transakce.|  
|TransactionScopeCurrentTransactionChanged|Upozornění|Původní aktuální TransactionTraceId ostatní TransactionTraceId|  
|TransactionScopeTimeout|Upozornění|Transactiontraceid jako obor "očekáván" aktuální transakce.|  
|DependentCloneCreated|Informace o|TransactionTraceId typ závislé transakce vytvořen (RollbackIfNotComplete/BlockCommitUntilComplete)|  
|DependentCloneComplete|Informace o|TransactionTraceId|  
|RecoveryComplete|Informace o|Identifikátor GUID správce prostředků (z base)|  
|Reenlist|Informace o|Identifikátor GUID správce prostředků (z base)|  
|TransactionSerialized|Informace o|TransactionTraceId.|  
|TransactionException|Chyba|Zpráva o výjimce|  
|InvalidOperationException|Chyba|Zpráva o výjimce|  
|InternalError|Kritická|Zpráva o výjimce|  
|TransferEvent||Pokud je transakcí deserializovat, nebo povýšen z <xref:System.Transactions> transakce distribuované jeden, jsou zapsány aktuální ID činnosti z kontextu ExecutionContext a ID distribuované transakce.<br /><br /> Když ovládacího prvku návrhu volá zpět do spravovaného kódu, ID distribuované transakce je nastaven jako ID činnosti v kontextu ExecutionContext po dobu trvání zpětného volání.|  
|ConfiguredDefaultTimeoutAdjusted|Upozornění|Žádná další data|  
|Vlastnost TransactionTimeout|Upozornění|TransactionTraceId transakce časový limit vypršel.|  
  
 Schématu XML pro všechny předchozí položky doplňující data má následující formát.  
  
### <a name="transactiontraceidentifier"></a>TransactionTraceIdentifier  
 `<TransactionTraceIdentifier>`  
  
 `<TransactionIdentifier >`  
  
 `string representation of transaction id`  
  
 `</TransactionIdentifier>`  
  
 `< CloneIdentifier >`  
  
 `the clone id number`  
  
 `</CloneIdentifier>`  
  
 `</TransactionTraceIdentifier>`  
  
### <a name="enlistmenttraceidentifier"></a>EnlistmentTraceIdentifier  
 `<EnlistmentTraceIdentifier>`  
  
 `<ResourceManagerId>`  
  
 `string form of guid`  
  
 `</ResourceManagerId>`  
  
 `<TransactionTraceIdentifier>`  
  
 `<TransactionIdentifier >`  
  
 `string representation of transaction id`  
  
 `</TransactionIdentifier>`  
  
 `<CloneIdentifier >`  
  
 `the clone id number`  
  
 `</CloneIdentifier>`  
  
 `<TransactionTraceIdentifier>`  
  
 `<EnlistmentIdentifier>`  
  
 `the enlistment id number`  
  
 `</EnlistmentIdentifier>`  
  
 `</EnlistmentTraceIdentifier>`  
  
### <a name="resource-manager-identifier"></a>Identifikátor správce prostředků  
 `<ResourceManagerId>`  
  
 `string form of guid`  
  
 `</ResourceManagerId>`  
  
## <a name="security-issues-for-tracing"></a>Potíže se zabezpečením pro trasování  
 Při jako správce zapnutí trasování, citlivými informacemi můžou zapíšou do protokolu trasování, který je veřejně zobrazitelné ve výchozím nastavení. Zmírnit všechny možné bezpečnostní riziko, měli byste zvážit ukládání protokol trasování v zabezpečeném umístění řídí sdílené složky a souboru systému přístupová oprávnění.
