---
title: Zabezpečení a uživatelský vstup
description: Váš kód může předat uživatelem zadaná data jako parametry jinému kódu, což může ovlivnit zabezpečení. Můžete provést kontrolu rozsahu a odmítnout problematický vstup.
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- security [.NET Framework], user input
- user input, security
- secure coding, user input
- code security, user input
ms.assetid: 9141076a-96c9-4b01-93de-366bb1d858bc
ms.openlocfilehash: fa9f8d4708e928c51e446d8369c9b4556fc6fb77
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186110"
---
# <a name="security-and-user-input"></a>Zabezpečení a uživatelský vstup

Uživatelská data, což je jakýkoli druh vstupu (data z webového požadavku nebo adresy URL, vstup do ovládacích prvků aplikace Microsoft Windows Forms a tak dále), mohou nepříznivě ovlivnit kód, protože často se tato data používají přímo jako parametry pro volání jiného kódu. Tato situace je obdobou škodlivého kódu, který volá váš kód s podivnými parametry, a měla by být přijata stejná opatření. Vstup uživatele je ve skutečnosti těžší, aby bezpečné, protože neexistuje žádný rámec zásobníku sledovat přítomnost potenciálně nedůvěryhodných dat.

Jedná se o jedny z nejjemnějších a nejtěžších chyb zabezpečení, které lze najít, protože i když mohou existovat v kódu, který zdánlivě nesouvisí se zabezpečením, jsou bránou pro předání chybná data do jiného kódu. Chcete-li hledat tyto chyby, postupujte podle jakéhokoli druhu vstupních dat, představte si, jaký rozsah možných hodnot může být a zvažte, zda kód, který vidí tato data, může zpracovat všechny tyto případy. Tyto chyby můžete opravit kontrolou rozsahu a odmítnutím jakéhokoli vstupu, který kód nemůže zpracovat.

Některé důležité aspekty týkající se uživatelských dat zahrnují následující:

- Všechna uživatelská data v odpovědi serveru jsou spuštěna v kontextu serveru v klientovi. Pokud webový server přebírá uživatelská data a vkládá je na vrácenou webovou stránku, může například obsahovat ** \<značku skriptu>** a spustit jako by ze serveru.

- Nezapomeňte, že klient může požádat o libovolnou adresu URL.

- Zvažte složité nebo neplatné cesty:

  - .. \ , extrémně dlouhé cesty.

  - Použití zástupných znaků (*).

  - Rozšíření tokenu (%token%).

  - Podivné formy cest se zvláštním významem.

  - Alternativní názvy datových `filename::$DATA`proudů systému souborů, například .

  - Krátké verze názvů souborů, `longfi~1` `longfilename`například pro .

- Nezapomeňte, že Eval(userdata) může dělat cokoliv.

- Buďte opatrní pozdní vazby na název, který obsahuje některá uživatelská data.

- Pokud máte co do činění s webovými daty, zvažte různé formy úniky, které jsou přípustné, včetně:

  - Šestnáctkové úniky (%nn).

  - Unicode unikne (%nnn).

  - Overlong UTF-8 escapes (%nn%nn).

  - Dvojité uniknutí (%nn se stane %mmnn, kde %mm je escape pro %').

- Buďte opatrní na uživatelská jména, která mohou mít více než jeden kanonický formát. Často můžete například použít formulář\\*uživatelského jména* MYDOMAIN nebo formulář *uživatelského jména.* @mydomain.example.com

## <a name="see-also"></a>Viz také

- [Pokyny pro zabezpečené kódování](../../../docs/standard/security/secure-coding-guidelines.md)
