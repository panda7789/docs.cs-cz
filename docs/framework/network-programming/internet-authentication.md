---
title: Ověřování v Internetu
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
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: e44d752e5743d7d56bdce9b216b4cf5f5f920734
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="internet-authentication"></a>Ověřování v Internetu
<xref:System.Net> Třídy podporují různé mechanismy ověřování klienta, včetně standardní Internet metod ověřování basic, algoritmem digest, vyjednávání protokolu NTLM a ověřování protokolu Kerberos, a také vlastních metod, které můžete vytvořit.  
  
 Pověření pro ověření jsou uložené v <xref:System.Net.NetworkCredential> a <xref:System.Net.CredentialCache> třídy, které implementují rozhraní <xref:System.Net.ICredentials> rozhraní. Když jedna z těchto tříd je dotazován na přihlašovací údaje, vrátí instanci **NetworkCredential** třídy. Spravuje proces ověřování <xref:System.Net.AuthenticationManager> třídy a proces skutečné ověřování se provádí třídou ověřování modul, který implementuje <xref:System.Net.IAuthenticationModule> rozhraní. Je nutné zaregistrovat vlastní ověřování modul s **třídě** před jeho použitím; vyjednávání moduly pro základní, algoritmus digest, protokol NTLM, a metody ověřování protokolu Kerberos je registrován ve výchozím nastavení.  
  
 **NetworkCredential** ukládá sadu přihlašovacích údajů spojených s jediný zdroj Internet identifikovaného identifikátorem URI a vrátí je v reakci na jakékoli volání <xref:System.Net.NetworkCredential.GetCredential%2A> metoda. **NetworkCredential** třída se obvykle používá aplikace, které přístup k omezenému počtu prostředků z Internetu nebo aplikace, které používají stejnou sadu přihlašovacích údajů ve všech případech.  
  
 **CredentialCache** třída ukládá kolekce přihlašovací údaje pro různé webové prostředky. Když <xref:System.Net.CredentialCache.GetCredential%2A> metoda je volána, **CredentialCache** vrátí správnou sadu přihlašovacích údajů, počítáno od identifikátor URI webové prostředky a požadovaná ověřovací schéma. Aplikace, které používají různých prostředků z Internetu pomocí různých ověřovacích schémata využívat **CredentialCache** třídy, protože ukládá všechny přihlašovací údaje a poskytuje je požadovaná.  
  
 Když internetových prostředků požaduje ověřování, <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType> metoda odešle <xref:System.Net.WebRequest> k **třídě** společně se žádostí pro přihlašovací údaje. Žádost je pak ověřit následujícím způsobem:  
  
1.  **Třídě** volání <xref:System.Net.IAuthenticationModule.Authenticate%2A> metoda na všech registrovaných ověřovací moduly v pořadí, které by bylo zaregistrováno. **Třídě** používá první modul, který nevrací **null** provést proces ověřování. Informace o procesu lišit v závislosti na typu zahrnutých ověřování modulu.  
  
2.  Po dokončení procesu ověřování modul ověřování vrátí <xref:System.Net.Authorization> k **WebRequest** obsahující informace potřebné pro přístup k Internetu prostředku.  
  
 Některé schémat ověřování, můžete ověřovat uživatele bez provedení první požadavek pro prostředek. Aplikace můžete ušetřit čas tím preauthenticating uživatele s hledaným prostředkem, a odstraňuje tak alespoň jeden odezvy na server. Nebo, aby byla později rychlejšího uživateli může provádět ověřování během spuštění programu. Schémat ověřování, které můžete použít sadu předběžného ověření <xref:System.Net.IAuthenticationModule.PreAuthenticate%2A> vlastnost **true**.  
  
## <a name="see-also"></a>Viz také  
 [Základní ověřování a ověřování algoritmem Digest](../../../docs/framework/network-programming/basic-and-digest-authentication.md)  
 [Ověřování NTLM a Kerberos](../../../docs/framework/network-programming/ntlm-and-kerberos-authentication.md)  
 [Zabezpečení v síťovém programování](../../../docs/framework/network-programming/security-in-network-programming.md)
