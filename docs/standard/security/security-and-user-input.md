---
title: "Zabezpečení a uživatelský vstup"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security [.NET Framework], user input
- user input, security
- secure coding, user input
- code security, user input
ms.assetid: 9141076a-96c9-4b01-93de-366bb1d858bc
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 157e20a80f0a76e157fad091bec6bfe635a9ccb8
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="security-and-user-input"></a>Zabezpečení a uživatelský vstup
Uživatelská data, která je jakýkoli druh vstupních (datových z webové žádosti nebo adresa URL, zadejte do ovládacích prvků formulářové aplikace Windows, a tak dále), může nepříznivě ovlivnit kód, protože často se budou používat přímo jako parametry pro volání jiného kódu. Tato situace je obdobou škodlivý kód volání kódu s neobvyklé parametry a stejná opatření by měla být provedena. Uživatelský vstup je ve skutečnosti těžší zabezpečit, protože neexistuje žádný rámec zásobníku pro sledování přítomnost potenciálně nedůvěryhodné data.  
  
 Toto jsou mezi chyby zabezpečení nejdelikátnější a nejtěžší najít, protože mohou existovat v kódu, který je zdánlivě nesouvisí se zabezpečením, jsou bránu chybná data prostřednictvím předat jiný kód. Chcete-li vyhledat tyto chyby, postupujte podle jakýkoli druh vstupních dat, představte si, co rozsahu možných hodnot může být a zvažte, zda kód zobrazuje tato data můžete zpracovat všechny tyto případy. Můžete je vyřešit tyto chyby prostřednictvím rozsah kontroly a odmítat všechny vstupní kód nelze zpracovat.  
  
 Některé důležité aspekty zahrnující uživatelská data zahrnují následující:  
  
-   Žádná data uživatelů v odpovědi serveru běží v kontextu serveru lokality na straně klienta. Pokud váš webový server zpracovává uživatelská data a vloží ho do vrácené webové stránky, může například obsahovat  **\<skriptu >** značky a spustit jako, pokud ze serveru.  
  
-   Mějte na paměti, že klient může vyžadovat libovolná adresa URL.  
  
-   Vezměte v úvahu podvodné nebo neplatné cesty:  
  
    -   .. \, extrémně dlouhé cesty.  
  
    -   Použití zástupných znaků (*).  
  
    -   Rozšíření tokenu (% token %).  
  
    -   Neobvyklé formy cesty se zvláštní význam.  
  
    -   Alternativní názvy datového proudu systému souborů, jako například `filename::$DATA`.  
  
    -   Krátké verze názvů souborů, například `longfi~1` pro `longfilename`.  
  
-   Mějte na paměti, že Eval(userdata) může udělat nic.  
  
-   Buďte opatrní, dynamické vazby název, který obsahuje některá uživatelská data.  
  
-   Pokud chcete pracovat s daty Web, zvažte různé formy řídicí sekvence, které jsou přípustné, včetně:  
  
    -   Šestnáctková řídicí sekvence (% nn).  
  
    -   Řídicí sekvence Unicode (% nnn).  
  
    -   Příliš dlouhého UTF-8 řídicí sekvence (% nn % nn).  
  
    -   Dvojité řídicí sekvence (% nn stane mmnn %, kde % mm je řídicí pro '%').  
  
-   Věnujte pozornost uživatelská jména, která může mít více než jeden kanonický formát. Například můžete často použít buď MOJEDOMÉNA\\*uživatelské jméno* formuláře nebo *uživatelské jméno* @mydomain.example.com formuláře.  
  
## <a name="see-also"></a>Viz také  
 [Pokyny pro zabezpečené kódování](../../../docs/standard/security/secure-coding-guidelines.md)
