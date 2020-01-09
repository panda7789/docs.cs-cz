---
title: Zabezpečení a uživatelský vstup
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- security [.NET Framework], user input
- user input, security
- secure coding, user input
- code security, user input
ms.assetid: 9141076a-96c9-4b01-93de-366bb1d858bc
ms.openlocfilehash: 0d34b06b44241feb7d6e3c8f76447b861563cfdc
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705857"
---
# <a name="security-and-user-input"></a>Zabezpečení a uživatelský vstup

Data uživatelů, což je jakýkoli druh vstupu (data z webového požadavku nebo adresy URL, vstup do ovládacích prvků aplikace Microsoft model Windows Forms a tak dále), mohou nepříznivě ovlivňovat kód, protože často se data používají přímo jako parametry pro volání jiného kódu. Tato situace je podobná škodlivému kódu volajícímu kód s neobvyklými parametry a je třeba vzít v nich stejná preventivní opatření. Vstup uživatele je ve skutečnosti těžší, protože není k dispozici žádný rámec zásobníku pro trasování přítomnosti potenciálně nedůvěryhodných dat.

Tyto chyby jsou z nejtěžších a nejzávažnější chyb zabezpečení, protože mohou existovat v kódu, který je zdánlivě nesouvisející se zabezpečením, jedná se o bránu pro předávání chybných dat do jiného kódu. Pokud chcete vyhledat tyto chyby, použijte libovolný druh vstupních dat, Představte si, co může být rozsah možných hodnot, a zvažte, jestli kód, který tato data zobrazuje, může zpracovat všechny tyto případy. Tyto chyby můžete opravit přes kontrolu rozsahu a odmítnutí jakéhokoli vstupu, který kód nemůže zpracovat.

Mezi důležité důležité informace týkající se uživatelských dat patří následující:

- Veškerá uživatelská data v reakci serveru běží v kontextu lokality serveru v klientovi. Pokud váš webový server přebírá data uživatelů a vkládá je do vrácené webové stránky, může například zahrnovat **> značku skriptu\<** a spustit jako if ze serveru.

- Pamatujte, že klient si může vyžádat libovolnou adresu URL.

- Zvažte štych nebo neplatné cesty:

  - .. \, extrémně dlouhé cesty.

  - Použití zástupných znaků (*).

  - Rozšíření tokenu (% token%)

  - Podivné formy cest se zvláštními významy.

  - Alternativní názvy datových proudů systému souborů, například `filename::$DATA`.

  - Krátké verze názvů souborů, například `longfi~1` pro `longfilename`.

- Mějte na paměti, že Eval (UserData) může dělat cokoli.

- Přistupují opatrně pozdní vazby na název, který obsahuje některá uživatelská data.

- Pokud pracujete s webovými daty, vezměte v úvahu různé formy řídicích znaků, které jsou povolené, včetně:

  - Šestnáctkové řídicí znaky (% NN).

  - Řídicí znaky Unicode (% NNN).

  - Nenáročné řídicí sekvence UTF-8 (% NN% NN).

  - Dvojité řídicí znaky (% NN se stávají% mmnn, kde% mm je řídicí znak pro%).

- Přistupují opatrně uživatelských jmen, která mohou mít více než jeden Kanonický formát. Například můžete často použít buď formulář MYDOMAIN\\*username* , nebo formulář *username*@mydomain.example.com.

## <a name="see-also"></a>Viz také:

- [Pokyny pro zabezpečené kódování](../../../docs/standard/security/secure-coding-guidelines.md)
