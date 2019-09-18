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
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71047910"
---
# <a name="internet-authentication"></a>Ověřování v internetu
<xref:System.Net> Třídy podporují různé mechanismy ověřování klientů, včetně standardních metod ověřování v Internetu Basic, Digest, Negotiate, NTLM a Kerberos a také vlastních metod, které můžete vytvořit.  
  
 Přihlašovací údaje pro ověřování jsou uloženy <xref:System.Net.NetworkCredential> v <xref:System.Net.CredentialCache> <xref:System.Net.ICredentials> třídách a, které implementují rozhraní. Pokud je jedna z těchto tříd dotazována pro přihlašovací údaje, vrátí instanci třídy **NetworkCredential** . Proces ověřování je spravován <xref:System.Net.AuthenticationManager> třídou a skutečný proces ověřování provádí třída ověřovacího modulu, která <xref:System.Net.IAuthenticationModule> implementuje rozhraní. Před použitím **správce AuthenticationManager** musíte zaregistrovat vlastní ověřovací modul. ve výchozím nastavení jsou zaregistrované moduly pro metody ověřování Basic, Digest, Negotiate, NTLM a Kerberos.  
  
 **NetworkCredential** ukládá sadu přihlašovacích údajů přidružených k jednomu internetovému prostředku identifikovanému identifikátorem URI a vrátí je jako odpověď na jakékoli volání <xref:System.Net.NetworkCredential.GetCredential%2A> metody. Třída **NetworkCredential** se obvykle používá aplikacemi, které přistupují k omezenému počtu internetových prostředků nebo aplikací, které používají stejnou sadu přihlašovacích údajů ve všech případech.  
  
 Třída **CredentialCache** ukládá kolekci přihlašovacích údajů pro různé webové prostředky. Když je metoda volána, CredentialCache vrátí správnou sadu přihlašovacích údajů, jak je určeno identifikátorem URI webového prostředku a požadované schéma ověřování. <xref:System.Net.CredentialCache.GetCredential%2A> Aplikace, které používají nejrůznější internetové prostředky s různými schématy ověřování, využívají používání třídy **CredentialCache** , protože ukládají všechny přihlašovací údaje a poskytují je podle požadavků.  
  
 Když prostředek v <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType> Internetu požaduje ověřování, metoda <xref:System.Net.WebRequest> pošle do **správce AuthenticationManager** spolu s požadavkem na přihlašovací údaje. Požadavek se pak ověří podle následujícího postupu:  
  
1. **Správce AuthenticationManager** volá <xref:System.Net.IAuthenticationModule.Authenticate%2A> metodu na všech registrovaných ověřovacích modulech v pořadí, v jakém byly registrovány. **Správce AuthenticationManager** používá první modul, který nevrací **hodnotu null** k provedení procesu ověřování. Podrobnosti o procesu se liší v závislosti na typu zapojeného modulu ověřování.  
  
2. Po dokončení procesu ověřování vrátí modul ověřování objekt <xref:System.Net.Authorization> **WebRequest** , který obsahuje informace potřebné pro přístup k internetovému prostředku.  
  
 Některá schémata ověřování mohou ověřit uživatele bez prvotního vytvoření žádosti o prostředek. Aplikace může ušetřit čas tím, že předověřuje uživatele s prostředkem, čímž eliminuje alespoň jednu zpáteční cestu k serveru. Nebo může provádět ověřování během spouštění programu, aby bylo možné později reagovat na uživatele. Schémata ověřování, která můžou použít předběžné ověřování, <xref:System.Net.IAuthenticationModule.PreAuthenticate%2A> nastaví vlastnost na **hodnotu true**.  
  
## <a name="see-also"></a>Viz také:

- [Základní ověřování a ověřování algoritmem Digest](basic-and-digest-authentication.md)
- [Ověřování NTLM a Kerberos](ntlm-and-kerberos-authentication.md)
- [Zabezpečení v síťovém programování](security-in-network-programming.md)
