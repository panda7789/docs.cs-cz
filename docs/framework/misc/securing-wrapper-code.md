---
title: Zabezpečení kódu obálky
ms.date: 03/30/2017
helpviewer_keywords:
- security [.NET Framework], wrapper code
- wrapper code, securing
- secure coding, wrapper code
- code security, wrapper code
ms.assetid: 1df6c516-5bba-48bd-b450-1070e04b7389
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e824fd686176d83c26ca2c042348c9423fbcc884
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69910743"
---
# <a name="securing-wrapper-code"></a>Zabezpečení kódu obálky
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 Kód obálky, zejména v případě, že má obálka vyšší důvěryhodnost než kód, který ho používá, může otevřít jedinečnou sadu slabých míst zabezpečení. Cokoli, co se provede jménem volajícího, kde omezená oprávnění volajícího nejsou zahrnutá do příslušné kontroly zabezpečení, představují potenciální slabá místa, která je možné zneužít.  
  
 Nikdy nepovolujte žádnou položku prostřednictvím obálky, kterou volající sám nevytvořil. Jedná se o zvláštní nebezpečí při provádění něčeho, co zahrnuje omezená kontrolu zabezpečení, a to na rozdíl od úplného požadavku na procházení zásobníku. V případě, že jsou zapojeny kontroly s jednou úrovní, může být při vzájemném navýšení kódu obálky mezi skutečným volajícím a prvkem rozhraní API snadno úspěšná kontrola zabezpečení, a to proto, že by to mělo oslabit zabezpečení.  
  
## <a name="delegates"></a>Delegáty  
 Zabezpečení delegáta se liší mezi verzemi .NET Framework.  Tato část popisuje různá chování delegátů a související otázky zabezpečení.  
  
### <a name="in-version-10-and-11-of-the-net-framework"></a>Ve verzi 1,0 a 1,1 .NET Framework  
 Verze 1,0 a 1,1 .NET Framework provádět následující akce zabezpečení proti tvůrci delegáta a volajícímu delegáta.  
  
- Při vytvoření delegáta je odkaz zabezpečení v metodě cíle delegáta proveden proti sadě udělení tvůrce delegáta.  Nepovedlo se splnit výsledky bezpečnostní akce v <xref:System.Security.SecurityException>.  
  
- Když je vyvolán delegát, jsou provedeny všechny existující požadavky zabezpečení na volajícím delegáta.  
  
 Pokaždé, když váš <xref:System.Delegate> kód trvá od méně důvěryhodného kódu, který by jej mohl zavolat, ujistěte se, že nepovolujete, aby se nepovolil méně důvěryhodný kód pro zvýšení jeho oprávnění. Pokud převezmete delegáta a použijete jej později, kód, který vytvořil delegáta, není v zásobníku volání a jeho oprávnění nebudou testována v případě, že se kód v rámci delegáta pokusí o chráněnou operaci. Pokud má váš kód a volající kód vyšší oprávnění než tvůrce, může tvůrce orchestrovat cestu volání, aniž by byla součástí zásobníku volání.  
  
### <a name="in-version-20-and-later-versions-of-the-net-framework"></a>Verze 2,0 a novější verze .NET Framework  
 Na rozdíl od předchozích verzí verze 2,0 a novější verze .NET Framework provádí akci zabezpečení proti tvůrci delegáta při vytvoření a volání delegáta.  
  
- Při vytvoření delegáta je odkaz zabezpečení v metodě cíle delegáta proveden proti sadě udělení tvůrce delegáta.  Nepovedlo se splnit výsledky bezpečnostní akce v <xref:System.Security.SecurityException>.  
  
- Sada udělení udělená tvůrci delegáta je také zachycena během vytváření delegáta a uložena společně s delegátem.  
  
- Když je delegát vyvolán, zachycená sada přidělení Tvůrce delegáta se nejprve vyhodnotí proti jakýmkoliv požadavkům v aktuálním kontextu, pokud tvůrce delegáta a volající patří do různých sestavení.  Dále jsou provedeny všechny existující požadavky zabezpečení na volajícím delegáta.  
  
## <a name="link-demands-and-wrappers"></a>Požadavky na propojení a obálky  
 Speciální případ ochrany s požadavky propojení byl posílen v infrastruktuře zabezpečení, ale stále je zdrojem možných slabých stránek v kódu.  
  
 Pokud plně důvěryhodný kód volá vlastnost, událost nebo metodu chráněnou [LinkDemand](../../../docs/framework/misc/link-demands.md), volání je úspěšné, pokud je splněna kontrolní oprávnění **LinkDemand** pro volajícího. Kromě toho, pokud plně důvěryhodný kód zveřejňuje třídu, která přebírá název vlastnosti a volá svůj přístupový objekt **Get** pomocí reflexe, volání metody **Get** je úspěšné, i když uživatelský kód nemá právo na přístup k této vlastnosti. Důvodem je, že **LinkDemand** kontroluje pouze bezprostředního volajícího, což je plně důvěryhodný kód. V podstatě plně důvěryhodný kód provádí privilegované volání jménem uživatelského kódu bez toho, aby se zajistilo, že kód uživatele má oprávnění k provedení tohoto volání.  
  
 Aby se zabránilo takovému bezpečnostnímu otvoru, modul CLR (Common Language Runtime) rozšiřuje kontrolu na úplný požadavek na procházení zásobníku na jakémkoli nepřímém volání metody, konstruktoru, vlastnosti nebo události chráněné **LinkDemand**. Tato ochrana má za následek nějaké náklady na výkon a mění sémantiku kontroly zabezpečení. úplný požadavek na procházení zásobníku může selhat, pokud by byla úspěšná i jedna úroveň kontroly.  
  
## <a name="assembly-loading-wrappers"></a>Sestavení – načítání obálek  
 Několik metod, které slouží k načtení spravovaného <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>kódu, včetně, načítají sestavení s legitimací volajícího. Pokud zabalíte některou z těchto metod, systém zabezpečení může použít udělení oprávnění vašeho kódu místo oprávnění volajícího na obálku pro načtení sestavení. Nepovolujte nedůvěryhodný kód pro načtení kódu, kterému je uděleno vyšší oprávnění než u volajícího pro vaši obálku.  
  
 Jakýkoli kód, který má úplný vztah důvěryhodnosti nebo významně vyšší důvěryhodnost než potenciální volající (včetně volajícího na úrovni internetových oprávnění), může tímto způsobem oslabit zabezpečení. Má-li váš kód veřejnou metodu, která přebírá bajtové pole a předá jej **sestavení. Load**, čímž se vytvoří sestavení za jménem volajícího, může dojít k přerušení zabezpečení.  
  
 Tento problém se týká následujících prvků rozhraní API:  
  
- <xref:System.AppDomain.DefineDynamicAssembly%2A?displayProperty=nameWithType>  
  
- <xref:System.AppDomain.Load%2A?displayProperty=nameWithType>  
  
- <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>  
  
- <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>  
  
## <a name="demand-vs-linkdemand"></a>Poptávka vs. LinkDemand  
 Deklarativní zabezpečení nabízí dva druhy kontrol zabezpečení, které jsou podobné, ale provádějí velmi odlišné kontroly. Oba formuláře byste měli pochopit, protože nesprávná volba může mít za následek slabou bezpečnost nebo ztrátu výkonu.  
  
 Deklarativní zabezpečení nabízí následující kontroly zabezpečení:  
  
- <xref:System.Security.Permissions.SecurityAction.Demand>Určuje procházení zásobníku zabezpečení přístupu kódu. Všichni volající v zásobníku musí mít zadané oprávnění nebo identitu předat. **Poptávka** probíhá při každém volání, protože zásobník může obsahovat různé volající. Při opakovaném volání metody se k této kontrole zabezpečení dojde pokaždé, když. **Poptávka** je dobrá ochrana před útoky luring; zjistí se neoprávněný kód, který se pokouší získat přes.  
  
- K [LinkDemand](../../../docs/framework/misc/link-demands.md) dojde v době kompilace JIT (just-in-time) a kontroluje pouze bezprostředního volajícího. Tato kontrolu zabezpečení nekontroluje volajícího volajícího. Po dokončení této kontroly se neúčtují žádné další nároky na zabezpečení bez ohledu na to, kolikrát volající může zavolat. Neexistuje ale ani ochrana před luring útoky. S **LinkDemand**, jakýkoliv kód, který projde test a může odkazovat na váš kód, může potenciálně přerušit zabezpečení tím, že umožňuje škodlivému kódu volat pomocí autorizovaného kódu. Proto nepoužívejte **LinkDemand** , pokud všechny možné slabiny nemůžete důkladně zabránit.  
  
    > [!NOTE]
    > V .NET Framework 4 byly požadavky propojení nahrazeny <xref:System.Security.SecurityCriticalAttribute> atributem v <xref:System.Security.SecurityRuleSet.Level2> sestaveních. <xref:System.Security.SecurityCriticalAttribute> Je ekvivalentem požadavku propojení pro úplný vztah důvěryhodnosti, ale má vliv také na pravidla dědičnosti. Další informace o této změně najdete v tématu [Kód transparentní pro zabezpečení, úroveň 2](../../../docs/framework/misc/security-transparent-code-level-2.md).  
  
 Další preventivní opatření nutná při použití **LinkDemand** musí být naprogramována individuálně; systém zabezpečení může pomáhat s vynucováním. Jakékoli omyly otevírá slabá místa zabezpečení. Veškerý autorizovaný kód, který používá váš kód, musí být zodpovědný za implementaci dalšího zabezpečení pomocí následujícího postupu:  
  
- Omezení přístupu volajícího kódu ke třídě nebo sestavení.  
  
- Umístěte stejné kontroly zabezpečení na volající kód, který se zobrazí na volaném kódu, a obligating jeho volajícím. Například pokud napíšete kód, který volá metodu, která je chráněna pomocí **LinkDemand** pro <xref:System.Security.Permissions.SecurityPermission> <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> se zadaným příznakem, vaše metoda by také měla vytvořit **LinkDemand** (nebo **poptávku**, která je silnější) pro tento udělen. Výjimkou je, že váš kód používá metodu chráněnou pomocí **LinkDemand**omezeného způsobu, jakým se rozhodnete, že je bezpečná, s ohledem na další mechanismy ochrany zabezpečení (například požadavky) ve vašem kódu. V tomto mimořádném případě volající vezme zodpovědnost za oslabení ochrany zabezpečení na základním kódu.  
  
- Zajištění, že volající vašeho kódu nemohou přesvědčit váš kód o volání chráněného kódu jménem. Jinými slovy volající nedokáže vynutit, aby ověřený kód předal konkrétní parametry do chráněného kódu nebo aby z něj byly vráceny výsledky.  
  
### <a name="interfaces-and-link-demands"></a>Požadavky na rozhraní a propojení  
 Pokud virtuální metoda, vlastnost nebo událost s **LinkDemand** přepisuje metodu základní třídy, musí mít metoda základní třídy také stejný **LinkDemand** pro potlačenou metodu, aby mohla být účinná. Škodlivý kód může přetypovat zpět na základní typ a volat metodu základní třídy. Všimněte si také, že požadavky na propojení lze přidat implicitně do sestavení, která nemají <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atribut na úrovni sestavení.  
  
 Je vhodné chránit implementace metod s požadavky propojení, pokud metody rozhraní také mají požadavky na propojení. Všimněte si následujících informací o použití požadavků na propojení s rozhraními:  
  
- Pokud umístíte **LinkDemand** do veřejné metody třídy, která implementuje metodu rozhraní, nebude možné **LinkDemand** vyhovět, pokud je pak přetypování na rozhraní a volání metody. V tomto případě vzhledem k tomu, že jste propojili rozhraní, je dodržen pouze **LinkDemand** v rozhraní.  
  
 Zkontrolujte následující položky pro problémy se zabezpečením:  
  
- Explicitní požadavky na propojení na metody rozhraní. Zajistěte, aby tyto požadavky na propojení nabízely očekávanou ochranu. Určete, zda škodlivý kód může pomocí přetypování získat odkaz na požadavky, jak je popsáno výše.  
  
- Virtuální metody s použitými požadavky propojení  
  
- Typy a rozhraní, která implementují. Ty by měly konzistentně používat požadavky na propojení.  
  
## <a name="see-also"></a>Viz také:

- [Pokyny pro zabezpečené kódování](../../standard/security/secure-coding-guidelines.md)
