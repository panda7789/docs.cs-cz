---
title: Data architektury služby
ms.date: 03/30/2017
ms.assetid: 2a2c8ddc-4e82-4e7f-a79f-97085c469517
ms.openlocfilehash: 5c65e9d473b5fe3f2b1c29824dcc1151abb0c3f6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61780804"
---
# <a name="service-framework-data"></a>Data architektury služby
Toto téma uvádí všechny výjimky generované Data architektury služby.  
  
## <a name="exception-list"></a>Seznam výjimek  
  
|Kód zdroje|Řetězec prostředku|  
|-------------------|---------------------|  
|AddressingExtensionInBadNS|Zadaný element v určeném oboru názvů není platný. To znamená, že zadaný prvek duplicitní prvek, že není platnou příponou protože elementy přípon nesmějí být v oboru názvů adresování.|  
|BinaryEncoderSessionInvalid|Relace binárního kodéru není platný, protože došlo k chybě dekódování předchozí zprávy.|  
|CannotDetectAddressingVersion|Nelze zjistit verzi elementu WS-Addressing. EndpointAddress nezačíná řetězcem elementu.|  
|CouldNotFindNamespaceForPrefix|Zadaná předpona neobsahuje žádnou vazbu oboru názvů v oboru.|  
|EncoderBadContentType|Nelze zpracovat a contentType.|  
|EncoderEnvelopeVersionMismatch|Verze obálky příchozí zprávy zadané neodpovídá určený kodek. Ujistěte se, že je vazba konfigurována se stejnou verzí jako očekávané zprávy.|  
|EncoderMessageVersionMismatch|Verze zadané odchozí zprávy neodpovídá určený kodek. Ujistěte se, že je vazba konfigurována se stejnou verzí jako zpráva.|  
|ExtraContentIsPresentInFaultDetail|Další obsah Extensible Markup Language se nachází v chybném detailním elementu. Je povolen pouze jeden element.|  
|FilterBadTableType|Třída IMessageFilterTable vytvořená pro filtr nemůže být třídou MessageFilterTable ani odvozený od třídy MessageFilterTable.|  
|FilterTableInvalidForLookup|Stav třídy MessageFilterTable je poškozený. Požadované hledání nelze provést.|  
|MandatoryHeaderNotUnderstood|Nejméně jeden požadovaný jednoduchý objekt přístup k protokolu záhlaví bloky se nerozpoznaly.|  
|MessageBodyIsStream|Text zprávy je datový proud.|  
|MessageBodyIsUnknown|Formát těla zprávy neznámý.|  
|MessageBodyReaderInvalidReadState|Nejde je využívat zadané třídě ReadState čtečky textu zprávy.|  
|MessageTextEncodingNotSupported|Zadaný text kódování, který se používá ve formátu textové zprávy není podporováno.|  
|MissingMessageID|Požadavku že chybí záhlaví třídy MessageID zprávy. Pro korelaci odpovědi je vyžadováno záhlaví třídy MessageID.|  
|MultipleMessageHeaders|Bylo nalezeno více záhlaví s určeným názvem a oborem názvů.|  
|MultipleMessageHeadersWithActor|Bylo nalezeno více záhlaví se zadaným názvem, obor názvů a role.|  
|MultipleRelatesToHeaders|Bylo nalezeno více záhlaví RelatesTo s Zadaný vztah. Pro každý vztah je povolený jenom jeden.|  
|QueryFunctionTypeNotSupported|Zadaný návratový typ hodnoty IXsltContextFunction není podporován.|  
|QueryIteratorOutOfScope|Objekt XPathNodeIterator byl označen jako neplatný. Třídy, které jsou předány jako argumenty IXsltContextFunctions XPathNodeIterators platí pouze v rámci této funkce. Nemůže být uložená v mezipaměti pro pozdější použití nebo vrácené funkcí.|  
|QueryVariableNull|Metody IXsltContextVariable nemůže vrátit hodnotu null.|  
|QueryVariableTypeNotSupported|Zadaný IXsltContextVariable odvozený typ není podporován.|  
|ReceiveShutdownReturnedMessage|Kanál přijal neočekávanou zprávu o zadávání s určenou akcí při zavírání. Zavřete kanál, jestliže neočekáváte další zprávy o zadávání.|  
|XmlBufferInInvalidState|Došlo k vnitřní chybě. Operaci nelze provést z důvodu stavu vyrovnávací paměť XML.|  
|XmlBufferQuotaExceeded|Velikost nutná k uložení obsahu Extensible Markup Language překročena kvóta vyrovnávací paměti.|
