---
title: "Overview2 zabezpečení"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 33e09965-61d5-48cc-9e8c-3b047cc4f194
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: d7288eeffeb642d1e897e11153802633d71747bd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="security-overview"></a>Přehled zabezpečení
Zabezpečení aplikace je nepřetržitý proces. Nikdy bude bod, kde vývojář může zaručit, že aplikace je bezpečné ze všech útoky, protože není možné předpovědět, jaké druhy budoucím útokům nové technologie povede. Naopak právě, protože nemá nikdo nedostatky zabezpečení ještě zjištěných (nebo publikovaná) v systému neznamená žádný existují nebo mohou existovat. Budete muset plánování zabezpečení během fáze návrhu projektu a také naplánovat, jak se zachová zabezpečení během životního cyklu aplikace.  
  
## <a name="design-for-security"></a>Návrh pro zabezpečení  
 Jeden z největších problémů při vývoji zabezpečení aplikací je, že zabezpečení je často chodím, něco implementovat po dokončení kód projektu. Vytváření není zabezpečení na aplikaci na začátku vede k nezabezpečené aplikace, protože nebyla zadána málo myšlenku kterým je aplikace zabezpečené.  
  
 Implementace zabezpečení poslední minutu vede k více chyb, jako zalomení software v části nová omezení, nebo musí být přepsány tak, aby dokázala pojmout neočekávané funkce. Každý jednotlivý řádek kódu revidovaný obsahuje možnost zavedení nové chyby. Z tohoto důvodu byste měli zvážit zabezpečení již v rané fázi v procesu vývoje, můžete pokračovat v kombinaci s vývojem nových funkcí.  
  
### <a name="threat-modeling"></a>Modelování hrozeb  
 Pokud nerozumíte možných útoků, které je vystaven nelze chránit systém proti útokům. Proces hodnocení bezpečnostní hrozby, nazývá *modelování hrozeb*, je třeba určit pravděpodobnost a následky narušení zabezpečení ve vaší aplikaci ADO.NET.  
  
 Modelování hrozeb se skládá ze tří kroků: Principy zobrazení nežádoucí osoba, charakterizuje zabezpečení systému a zjišťování hrozeb.  
  
 Modelování hrozeb je iterativní přístup k vyhodnocování ohrožení zabezpečení ve vaší aplikaci a zjistěte, které jsou nejvíce nebezpečné, protože potenciálně zobrazovat nejcitlivější data. Po identifikování chyb zabezpečení, můžete je zařadit v pořadí podle závažnosti a vytvořit sadu protiopatření pro čítače hrozby seřazený podle priority.  
  
 Další informace najdete v následujících zdrojích informací.  
  
|Prostředek|Popis|  
|--------------|-----------------|  
|[Modelování hrozeb](http://go.microsoft.com/fwlink/?LinkId=98353) webu v Centru pro vývojáře MSDN zabezpečení|Prostředky na této stránce vám pomůže pochopit riziko, že proces modelování a vytvářet modely hrozeb, které můžete použít k zabezpečení vaše vlastní aplikace|  
  
## <a name="the-principle-of-least-privilege"></a>Princip nejnižších nutných oprávnění  
 Při návrhu, vytvoření a nasazení aplikace, musí předpokládat, že vaše aplikace bude napadení. Tyto útoky často pocházet z škodlivý kód, který se spustí s oprávněními uživatel, který spouští kód. Ostatní můžete pocházejí z úmyslného kód, který má byla zneužití uživatelem se zlými úmysly. Při plánování zabezpečení, vždy předpokládejte, že dojde k nejhorším případě.  
  
 Jeden protiopatření, které můžete použít se pokusí postavit tolik bariéry kolem kódu nejdříve spuštěním s nejnižší oprávnění. Princip nejnižších nutných oprávnění říká, že všechna oprávnění, která daný udělení minimem kódu, které jsou nezbytné pro nejkratší doba, která je nutný k provedení úlohy.  
  
 Doporučený postup pro vytváření zabezpečených aplikací má začínat vůbec žádná oprávnění a poté přidejte nejbližší oprávnění pro provedení úkolu během provádění. Naopak počínaje všechna oprávnění a potom odepření jednotlivých ty vede k nezabezpečené aplikace, které je obtížné testování a udržovat, protože celistvosti může existovat z neúmyslnému přidělování větší oprávnění než nezbytné.  
  
 Další informace o zabezpečení vaší aplikací najdete v následujících zdrojích informací.  
  
|Prostředek|Popis|  
|--------------|-----------------|  
|[Zabezpečení aplikací](/visualstudio/ide/securing-applications)|Obsahuje odkazy na témata obecné zabezpečení. Obsahuje taky odkazy na témata pro zabezpečení distribuovaných aplikací, webových aplikací, mobilní aplikace a aplikací klasické pracovní plochy.|  
  
## <a name="code-access-security-cas"></a>Zabezpečení přístupu kódu (CAS)  
 Zabezpečení přístupu kódu (CAS) je mechanismus, který pomáhá omezit přístup k chráněným prostředkům a operace. Certifikační Autority v rozhraní .NET Framework, provádí následující funkce:  
  
-   Definuje oprávnění a sady oprávnění, které představují práva pro přístup k různým prostředkům systému.  
  
-   Umožňuje správci nakonfigurovat zásady zabezpečení tím, že přidružíte sady oprávnění se skupinami kódu (skupiny kódu).  
  
-   Umožňuje kód požádat o oprávnění vyžaduje, aby bylo možné spustit, jakož i oprávnění, které by byly užitečné používat a určuje, jaká oprávnění kód musí mít nikdy.  
  
-   Uděluje oprávnění pro každé sestavení, které je načtena, na základě oprávnění požadovaná tímto kódem a na operace povolené zásady zabezpečení.  
  
-   Umožňuje kódu požadovat, aby jeho volající mít specifické oprávnění.  
  
-   Umožňuje kódu požadovat, jeho volající měl digitální podpis, což umožňuje volání chráněného kódu pouze volajícím z určité organizace nebo webu.  
  
-   Porovnání udělená oprávnění každého volajícího v zásobníku volání oprávnění, které volající musí mít vynucuje omezení kódu v době běhu.  
  
 Chcete-li minimalizovat objem škody, které může dojít, pokud se podaří útoku, zvolte kontext zabezpečení pro váš kód, který uděluje přístup pouze k prostředkům, musí ke své práci Hotovo a žádné další.  
  
 Další informace najdete v následujících zdrojích informací.  
  
|Prostředek|Popis|  
|--------------|-----------------|  
|[Zabezpečení přístupu kódu a ADO.NET](../../../../docs/framework/data/adonet/code-access-security.md)|Popisuje interakce mezi zabezpečení přístupu kódu, na základě rolí zabezpečení a částečně důvěryhodného prostředí z hlediska aplikace ADO.NET.|  
|[Zabezpečení přístupu kódu](http://msdn.microsoft.com/en-us/23a20143-241d-4fe5-9d9f-3933fd594c03)|Obsahuje odkazy na další témata s popisem certifikační Autority v rozhraní .NET Framework.|  
  
## <a name="database-security"></a>Zabezpečení databáze  
 Princip nejnižších nutných oprávnění platí také pro zdroj dat. Některé obecné pokyny pro zabezpečení databáze patří:  
  
-   Vytvořte účty s nejnižšími možnými oprávněními.  
  
-   Nepovolte uživatelům přístup k účty pro správu jenom k začít pracovat kódu.  
  
-   Nevrátí serverové chybové zprávy pro klientské aplikace.  
  
-   Ověřte všechny vstupu v klientovi i na serveru.  
  
-   Použít parametrizované příkazy a vyhnout se dynamických příkazů SQL.  
  
-   Povolte zabezpečení, auditování a protokolování pro databázi, kterou používáte tak, aby upozorní na jakékoli porušení zabezpečení.  
  
 Další informace najdete v následujících zdrojích informací.  
  
|Prostředek|Popis|  
|--------------|-----------------|  
|[Zabezpečení SQL serveru](../../../../docs/framework/data/adonet/sql/sql-server-security.md)|Poskytuje přehled zabezpečení systému SQL Server s aplikačními scénáři, které obsahují pokyny pro vytváření aplikací pro zabezpečené ADO.NET cílených systému SQL Server.|  
|[Doporučení pro strategií přístupu dat](http://msdn.microsoft.com/en-us/72411f32-d12a-4de8-b961-e54fca7faaf5)|Poskytuje doporučení pro přístup k datům a provádění databázových operací.|  
  
## <a name="security-policy-and-administration"></a>Zásady zabezpečení a správy  
 Nesprávná Správa zásady (CAS) zabezpečení přístupu kódu může potenciálně vytvořit slabá místa zabezpečení. Jakmile je aplikace nasazena, by měl použít techniky pro monitorování zabezpečení a rizika vyhodnoceny jako nové hrozby vznikat.  
  
 Další informace najdete v následujících zdrojích informací.  
  
|Prostředek|Popis|  
|--------------|-----------------|  
|[NIB: Správa zásad zabezpečení](http://msdn.microsoft.com/en-us/d754e05d-29dc-4d3a-a2c2-95eaaf1b82b9)|Obsahuje informace o vytváření a správu zásad zabezpečení.|  
|[NIB: Osvědčené postupy pro zásady zabezpečení](http://msdn.microsoft.com/en-us/d49bc4d5-efb7-4caa-a2fe-e4d3cec63c05)|Obsahuje odkazy popisující, jak spravovat zásady zabezpečení.|  
  
## <a name="see-also"></a>Viz také  
 [Zabezpečení aplikací ADO.NET](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [Připravte si kód pro rozhraní .NET Framework a zabezpečení v nativním režimu](http://msdn.microsoft.com/en-us/bd61be84-c143-409a-a75a-44253724f784)  
 [Zabezpečení SQL serveru](../../../../docs/framework/data/adonet/sql/sql-server-security.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
