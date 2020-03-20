---
title: Ověřování v internetu
ms.date: 03/30/2017
helpviewer_keywords:
- authentication [.NET Framework], classes
- IAuthenticationModule interface
- ICredentialLookup interface
- CredentialCache class, about CredentialCache class
- receiving data, authentication
- AuthenticationManager class, about AuthenticationManager class
- Internet, authentication
- sending data, authentication
- network resources, authentication
- user authentication, classes for authentication
- NetworkCredential class, about NetworkCredential class
- client authentication, classes for authentication
ms.assetid: d342e87c-f672-4660-a513-41a2f2b80c4a
ms.openlocfilehash: 3e0b5cd58270cec758db5d4dad6f3ad48962921a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "71047910"
---
# <a name="internet-authentication"></a>Ověřování v internetu
Třídy <xref:System.Net> podporují různé mechanismy ověřování klientů, včetně standardních metod ověřování v Internetu základní, digest, vyjednávat, NTLM a Kerberos ověřování, stejně jako vlastní metody, které můžete vytvořit.  
  
 Ověřovací pověření jsou <xref:System.Net.NetworkCredential> uloženy <xref:System.Net.CredentialCache> v a <xref:System.Net.ICredentials> třídy, které implementují rozhraní. Pokud je jedna z těchto tříd dotazována na pověření, vrátí instanci třídy **NetworkCredential.** Proces ověřování je spravován <xref:System.Net.AuthenticationManager> třídou a skutečný proces ověřování je prováděn třídou <xref:System.Net.IAuthenticationModule> ověřovacího modulu, která implementuje rozhraní. Před použitím nástroje AuthenticationManager je nutné zaregistrovat vlastní ověřovací modul u **nástroje AuthenticationManager.** moduly pro základní, digest, vyjednávat, NTLM a Kerberos metody ověřování jsou registrovány ve výchozím nastavení.  
  
 **NetworkCredential** ukládá sadu pověření přidružených k jednomu prostředku Sítě Internet identifikovaným identifikátorem <xref:System.Net.NetworkCredential.GetCredential%2A> URI a vrátí je jako odpověď na jakékoli volání metody. Třída **NetworkCredential** je obvykle používána aplikacemi, které přistupují k omezenému počtu internetových prostředků, nebo aplikacemi, které ve všech případech používají stejnou sadu pověření.  
  
 Třída **CredentialCache** ukládá kolekci pověření pro různé webové prostředky. Při <xref:System.Net.CredentialCache.GetCredential%2A> volání metody **vrátí credentialcache** správnou sadu pověření, jak je určeno identifikátorem URI webového prostředku a požadované schéma ověřování. Aplikace, které používají různé internetové prostředky s různými schématy ověřování, mají prospěch z použití třídy **CredentialCache,** protože ukládá všechna pověření a poskytuje je podle požadavků.  
  
 Když internetový prostředek požaduje ověření, <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType> metoda <xref:System.Net.WebRequest> odešle správce **ověřování** spolu s požadavkem na pověření. Požadavek je pak ověřen následujícím postupem:  
  
1. **Správce ověřování** volá <xref:System.Net.IAuthenticationModule.Authenticate%2A> metodu pro každý z registrovaných ověřovacích modulů v pořadí, v jakém byly zaregistrovány. **Správce ověřování** používá první modul, který nevrací **hodnotu null** k provedení procesu ověřování. Podrobnosti procesu se liší v závislosti na typu autentizačního modulu.  
  
2. Po dokončení procesu ověřování vrátí ověřovací <xref:System.Net.Authorization> modul **a webRequest,** který obsahuje informace potřebné pro přístup k prostředku Sítě Internet.  
  
 Některá schémata ověřování můžete ověřit uživatele bez předchozího podání požadavku na prostředek. Aplikace může ušetřit čas tím, že předem osunutí uživatele s prostředek, čímž se eliminuje alespoň jeden zpáteční cestu na server. Nebo může provádět ověřování během spuštění programu, aby byl později lépe reagující na uživatele. Schémata ověřování, která mohou <xref:System.Net.IAuthenticationModule.PreAuthenticate%2A> používat předběžné ověřování, nastavují vlastnost na **hodnotu true**.  
  
## <a name="see-also"></a>Viz také

- [Základní a digest ověřování](basic-and-digest-authentication.md)
- [Ověřování NTLM a Kerberos](ntlm-and-kerberos-authentication.md)
- [Zabezpečení v síťovém programování](security-in-network-programming.md)
