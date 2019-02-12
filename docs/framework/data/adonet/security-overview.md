---
title: Overview2 zabezpečení
ms.date: 03/30/2017
ms.assetid: 33e09965-61d5-48cc-9e8c-3b047cc4f194
ms.openlocfilehash: 0b5b86aad2365c76351ff748228826ba703223dc
ms.sourcegitcommit: d2ccb199ae6bc5787b4762e9ea6d3f6fe88677af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/12/2019
ms.locfileid: "56091796"
---
# <a name="security-overview"></a>Přehled zabezpečení
Zabezpečení aplikace je soustavný proces. Nikdy bude do bodu, kdy vývojář může zaručit, že je aplikace bezpečné útoky, protože není možné předpovědět, jaké druhy nové technologie budoucím útokům přinese. Naopak pouze z důvodu nemá nikdo chybám zabezpečení ještě zjištěných (nebo publikovaná) v systému neznamená, že žádný neexistuje, nebo může existovat. Budete muset plánování zabezpečení během fáze návrhu projektu, jakož i plánování, jak se zachová zabezpečení během životního cyklu aplikace.  
  
## <a name="design-for-security"></a>Návrh pro zajištění zabezpečení  
 Jeden z největších problémů při vývoji bezpečných aplikací je zabezpečení je často opomíjet něco, co můžete implementovat po dokončení kódu projektu. Není vytváření zabezpečení do aplikace zaměřeným na vede k nezabezpečené aplikace, protože bylo přiděleno trochu přiměje Čím aplikace zabezpečené.  
  
 Implementace zabezpečení poslední minutu vede k více chyb, jako konce software v části nová omezení nebo má přepsat tak, aby vyhovovaly neočekávané funkce. Každý jednotlivý řádek upravený kód obsahuje možnost zavlečení nových chyb. Z tohoto důvodu byste měli zvážit zabezpečení v rané fázi vývojového procesu, můžete pokračovat v kombinaci s vývojem nových funkcí.  
  
### <a name="threat-modeling"></a>Modelování hrozeb  
 Systém proti útoku nelze chránit, pokud nerozumíte potenciální útoky, které je přístupný. Proces hodnocení ohrožení zabezpečení, nazývá *modelování hrozeb*, je třeba určit pravděpodobnost, že a důsledky porušením zabezpečení v aplikaci ADO.NET.  
  
 Modelování hrozeb se skládá ze tří kroků: Principy zobrazení nežádoucí osoby, charakterizuje zabezpečení systému a zjištění hrozby.  
  
 Modelování ohrožení je iteračního postupu pro posouzení ohrožení zabezpečení v aplikaci najít ty, které jsou nejvíce nebezpečné, protože zveřejňovaly nejcitlivější data. Po identifikování chyb zabezpečení Ohodnoťte je podle závažnosti a vytvořit seřazený podle priority sadu protiopatření čítači hrozby.  
  
 Další informace najdete v následujících materiálech.  
  
|Prostředek|Popis|  
|--------------|-----------------|  
|[Pro modelování hrozeb](https://go.microsoft.com/fwlink/?LinkId=98353) lokality na Security Center pro vývojáře MSDN|Prostředky na této stránce vám pomůže porozumět před internetovými útoky proces modelování a vytvářet modely hrozeb, které můžete použít k zabezpečení vašich vlastních aplikací|  
  
## <a name="the-principle-of-least-privilege"></a>Princip nejnižších oprávnění  
 Když navrhovat, sestavovat a nasazovat aplikace, musíte předpokládat, že vaše aplikace bude napaden. Tyto útoky často pocházejí od škodlivý kód, který se spustí s oprávněním uživatel, který spouští kód. Ostatní můžou pocházet úmyslného kódem, který má byla ze strany útočníka zneužít. Při plánování zabezpečení, vždy předpokládejte, že že nejhorším případě dojde.  
  
 Jeden protiopatření, které můžete použít je pokusit se postavit tolik stěn kolem kódu nejvíce spuštěním s nejnižšími oprávněními. Princip nejnižších oprávnění říká, že všechna oprávnění, která daný udělení minimální množství kódu potřebného pro nejkratší dobu trvání doby potřebné k dosažení.  
  
 Osvědčené postupy pro vytváření zabezpečených aplikací má začínat vůbec žádná oprávnění a pak přidejte nejužší oprávnění pro konkrétní úkol právě probíhá. Naopak počínaje všechna oprávnění a pak zamítnutí jednotlivých ty vede k nezabezpečené aplikace, které je obtížné pro testování a udržovat, protože můžou existovat bezpečnostní díry neúmyslně poskytnout větší oprávnění než nezbytné.  
  
 Další informace o zabezpečení vašich aplikací najdete v následující prostředky.  
  
|Prostředek|Popis|  
|--------------|-----------------|  
|[Zabezpečování aplikací](/visualstudio/ide/securing-applications)|Obsahuje odkazy na témata o obecných zabezpečení. Obsahuje taky odkazy na témata pro zabezpečení distribuované aplikace, webové aplikace, mobilní aplikace a desktopové aplikace.|  
  
## <a name="code-access-security-cas"></a>Zabezpečení přístupu kódu (CAS)  
 Zabezpečení přístupu kódu (CAS) je mechanismus, který pomáhá omezit přístup, který má kód k chráněným prostředkům a operacím. V rozhraní .NET Framework certifikačních Autorit provádí následující funkce:  
  
-   Definuje oprávnění a sady oprávnění, které představují práva pro přístup k různým prostředkům systému.  
  
-   Umožňuje správcům konfigurovat zásady zabezpečení tím, že přidružíte sady oprávnění se skupinami kódu (skupiny kódu).  
  
-   Umožňuje kódu požádat o oprávnění vyžaduje, aby bylo možné spustit, jakož i oprávnění, která může být užitečné mít a určuje, jaká oprávnění kód musí mít nikdy.  
  
-   Uděluje oprávnění ke každému sestavení, který je načten, na základě oprávnění požadovaná tímto kódem a na operace povolena zásadami zabezpečení.  
  
-   Umožňuje poptávku, že jeho volající nemá oprávnění kódu.  
  
-   Umožňuje kódu na vyžádání, že jeho volající nemá digitální podpis, což umožní volat chráněné kód pouze volající z konkrétní organizace nebo webu.  
  
-   Vynucuje omezení kódu v době běhu porovnáním udělená oprávnění každý volající v zásobníku volání, které volající musí mít oprávnění.  
  
 Chcete-li minimalizovat množství škody, které může dojít, pokud útok úspěšně, zvolte kontext zabezpečení pro kód, který uděluje přístup jenom na prostředky, které potřebuje ke své práci Hotovo a nesmí mít víc.  
  
 Další informace najdete v následujících materiálech.  
  
|Prostředek|Popis|  
|--------------|-----------------|  
|[Zabezpečení přístupu ke kódu a ADO.NET](../../../../docs/framework/data/adonet/code-access-security.md)|Najdete popis interakcí mezi zabezpečení přístupu kódu, na základě rolí zabezpečení a částečně důvěryhodného prostředí z hlediska aplikaci ADO.NET.|  
|[Zabezpečení přístupu kódu](../../../../docs/framework/misc/code-access-security.md)|Obsahuje odkazy na další témata popisující certifikační Autority v rozhraní .NET Framework.|  
  
## <a name="database-security"></a>Zabezpečení databáze  
 Princip nejnižších oprávnění platí také pro zdroj dat. Některé obecné pokyny pro zabezpečení databáze patří:  
  
-   Vytvoření účtů s nejnižší možná oprávnění.  
  
-   Nepovolte uživatelům přístup k účtům správců jen k získání kódu.  
  
-   Nevkládejte do klientské aplikace na straně serveru chybové zprávy.  
  
-   Ověřte všechny vstupy u klienta a serveru.  
  
-   Používat příkazy s parametry a vyhnout se dynamické příkazů jazyka SQL.  
  
-   Povolte zabezpečení, auditování a protokolování pro databáze, kterou používáte tak, aby se zobrazí upozornění na jakékoli porušením zabezpečení.  
  
 Další informace najdete v následujících materiálech.  
  
|Prostředek|Popis|  
|--------------|-----------------|  
|[SQL Server – zabezpečení](../../../../docs/framework/data/adonet/sql/sql-server-security.md)|Poskytuje přehled zabezpečení systému SQL Server s aplikačními scénáři, které poskytují pokyny pro vytváření zabezpečených aplikací ADO.NET, které cílí na systém SQL Server.|  
|[Doporučení pro strategií přístupu dat](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/8fxztkff(v=vs.90))|Poskytuje doporučení pro přístup k datům a provádění databázových operací.|  
  
## <a name="security-policy-and-administration"></a>Zásady zabezpečení a Správa  
 Nesprávně správu zásad zabezpečení (CAS) pro přístup kód by mohl vytvořit slabé stránky zabezpečení. Jakmile je aplikace nasazená, se má použít techniky pro monitorování zabezpečení a tom rizika vyhodnotí jako nové hrozby.  
  
 Další informace najdete v následujících materiálech.  
  
|Prostředek|Popis|  
|--------------|-----------------|  
|[Správa zásad zabezpečení](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/c1k0eed6(v=vs.100))|Obsahuje informace o vytváření a správě zásad zabezpečení.|  
|[Doporučené postupy zabezpečení pro zásady](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sa4se9bc(v=vs.100))|Obsahuje odkazy, které popisují, jak spravovat zásady zabezpečení.|  
  
## <a name="see-also"></a>Viz také:
- [Zabezpečení aplikací ADO.NET](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)
- [Zabezpečení v rozhraní .NET](../../../standard/security/index.md)
- [SQL Server – zabezpečení](../../../../docs/framework/data/adonet/sql/sql-server-security.md)
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
