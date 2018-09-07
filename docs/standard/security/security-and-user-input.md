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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 27818d5e1779cd6e10e11830f91a20a3e638639a
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44066513"
---
# <a name="security-and-user-input"></a>Zabezpečení a uživatelský vstup
Uživatelská data, která je jakýkoli druh vstupních (datových z webového požadavku nebo adresu URL, vstupní ovládací prvky aplikace Microsoft Windows Forms a tak dále), může nepříznivě ovlivnit kód, protože často tato data se používají přímo jako parametry pro volání jiného kódu. Tato situace je obdobou škodlivý kód volá váš kód s neznámé parametry a stejná opatření by měl být přijata. Uživatelský vstup je ve skutečnosti obtížnější zabezpečit, protože neexistuje žádný rámce zásobníku trasování na přítomnost potenciálně nedůvěryhodná data.  
  
 Toto jsou mezi zabezpečení nejdelikátnější a těch nejtěžších chyb najít, protože mohou existovat v kódu, který je zdánlivě nesouvisí se zabezpečením, jsou brána chybná data prostřednictvím předat jiným kódem. K vyhledání těchto chyb, postupujte podle všech typů vstupních dat, představte si, co rozsah možných hodnot může být a zvažte, zda kód zobrazení těchto dat může zpracovávat všechny tyto případy. Můžete vyřešit tyto chyby prostřednictvím rozsah kontroly odhalovat a odmítat jakéhokoliv vstupu, který nemůže zpracovat kód.  
  
 Některé důležité informace týkající se uživatelská data zahrnují následující:  
  
-   Žádná data uživatelů v odpovědi na serveru běží v kontextu na server lokality na straně klienta. Pokud váš webový server přijímá data uživatele a vloží jej do vrácené webové stránce, může například obsahovat  **\<skript >** označit a spustit jako by ze serveru.  
  
-   Mějte na paměti, že klient může požádat o libovolnou adresu URL.  
  
-   Vezměte v úvahu cesty záludné nebo je neplatný:  
  
    -   .. \, velmi dlouhé cesty.  
  
    -   Použití zástupných znaků (*).  
  
    -   Rozšíření token (token %).  
  
    -   Neobvyklé formy cesty se zvláštní význam.  
  
    -   Alternativní názvy stream systému souborů, jako například `filename::$DATA`.  
  
    -   Krátká verze názvů souborů, jako `longfi~1` pro `longfilename`.  
  
-   Mějte na paměti, že Eval(userdata) může dělat něco.  
  
-   Dávejte pozor na název, který obsahuje některá uživatelská data z pozdní vazby.  
  
-   Pokud pracujete s daty Web, zvažte možnost různé formy řídící znaky, které jsou přípustné, včetně:  
  
    -   Šestnáctková řídicí sekvence (% nn).  
  
    -   Řídicí sekvence Unicode (% nnn).  
  
    -   Příliš dlouhého UTF-8 řídicí sekvence (% nn % nn).  
  
    -   Dvojité řídicí sekvence (% nn stane mmnn %, kde je % mm řídicí pro '%').  
  
-   Dávejte pozor na uživatelská jména, která může mít více než jeden kanonický formát. Například můžete často použít buď MOJEDOMÉNA\\*uživatelské jméno* formuláře nebo *uživatelské jméno* @mydomain.example.com formuláře.  
  
## <a name="see-also"></a>Viz také:

- [Pokyny pro zabezpečené kódování](../../../docs/standard/security/secure-coding-guidelines.md)
