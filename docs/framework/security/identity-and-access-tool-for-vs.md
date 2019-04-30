---
title: Nástroj Identita a přístup pro Visual Studio 2012
ms.date: 03/30/2017
ms.assetid: 87b8f8f2-4074-44fd-9fd6-08278e877390
author: BrucePerlerMS
ms.openlocfilehash: 65d771b87cd3198848ffac387446abb17df18250
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61940410"
---
# <a name="identity-and-access-tool-for-visual-studio-2012"></a>Nástroj Identita a přístup pro Visual Studio 2012
Toto téma popisuje nový nástroj Identity and Access Tool for Visual Studio 11. Tento nástroj si můžete stáhnout z následující adresy URL: <https://go.microsoft.com/fwlink/?LinkID=245849> nebo přímo v rámci sady Visual Studio 11 tak, že "identity" ve Správci rozšíření.  
  
 Nástroj Identity and Access Tool for Visual Studio 11 přináší výrazně jednodušší možnosti vývoje díky následujícím hlavním funkcím:  
  
- Pomocí tohoto nového nástroje můžete vyvíjet s použitím typů projektů webových aplikací a cílit při tom na službu IIS Express.  
  
- Na rozdíl od obecného ověřování, které jen poskytuje ochranu, můžete pomocí nového nástroje určit svou stránku zjišťování/kontroler místní domovské sféry (nebo jiný koncový bod, který zajišťuje ověřování ve vaší aplikaci) a technologie WIF nakonfiguruje všechny neověřené žádosti tak, aby byly zasílány na toto místo namísto jejich přesměrování do služby STS.  
  
- Nástroj obsahuje testovací službu tokenů zabezpečení (STS), která se po zahájení ladicí relace spustí v místním počítači. Proto již nemusíte vytvářet vlastní projekty STS a upravovat je tak, abyste získali deklarace potřebné k testování vašich aplikací. Typy a hodnoty deklarací jsou plně přizpůsobitelné.  
  
- Můžete upravit běžná nastavení přímo prostřednictvím uživatelského rozhraní nástroje, aniž byste museli upravovat soubor web.config.  
  
- Můžete vytvořit federaci se službou Active Directory Federation Services (AD FS) 2.0 (nebo jinými poskytovateli identit podporujícími protokol WS-Federation) na jedné obrazovce.  
  
- Nástroj využívá funkce sady Windows Azure Access Control Service (ACS) prostřednictvím jednoduchého seznamu zaškrtávacích políček pro všechny poskytovatele identit, které chcete použít: Facebook, Google, Live ID, Yahoo!, jakýkoli poskytovatel OpenID a jakýkoli poskytovatel WS-Federation. Vyberte poskytovatele identity, klikněte na tlačítko OK a poté stiskněte klávesu F5. Vaše aplikace i služba ACS budou automaticky nakonfigurovány a vaše testovaná aplikace bude pracovat se službou ACS.  
  
## <a name="see-also"></a>Viz také:

- [Funkce technologie WIF](../../../docs/framework/security/wif-features.md)
