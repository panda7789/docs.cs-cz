---
title: Přehled zabezpečení
ms.date: 03/30/2017
helpviewer_keywords:
- code access security [Windows Forms], Windows Forms
- permissions [Windows Forms], Windows Forms
- Windows Forms, security
- security [Windows Forms], about security
- access control [Windows Forms], Windows Forms
ms.assetid: 4810dc9f-ea23-4ce1-8ea1-657f0ff1d820
ms.openlocfilehash: 9010b45383f856079661359fdf82180526d96dde
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76734853"
---
# <a name="security-in-windows-forms-overview"></a>Přehled zabezpečení ve Windows Forms

Před vydáním .NET Framework měl veškerý kód spuštěný v počítači uživatele stejná práva nebo oprávnění pro přístup k prostředkům, které měl uživatel počítače. Pokud má uživatel například povolený přístup k systému souborů, kód byl povolen pro přístup k systému souborů; Pokud má uživatel povolený přístup k databázi, kód byl povolen pro přístup k této databázi. I když tato práva nebo oprávnění mohou být přijatelná pro kód ve spustitelných souborech, které uživatel explicitně nainstaloval do místního počítače, nemusí být přijatelné pro potenciálně škodlivý kód pocházející z Internetu nebo místního intranetu. Tento kód by neměl mít přístup k prostředkům počítače uživatele bez oprávnění.

.NET Framework zavádí infrastrukturu označovanou jako zabezpečení přístupu kódu, která umožňuje odlišit oprávnění nebo práva k tomuto kódu z práv, která má uživatel. Ve výchozím nastavení se kód pocházející z Internetu a intranetu dá spustit jenom v tom, co se říká částečná důvěryhodnost. Částečně důvěryhodné subjekty aplikace na řadu omezení: mimo jiné má aplikace omezený přístup k místnímu pevnému disku a nemůže spustit nespravovaný kód. .NET Framework řídí prostředky, ke kterým má kód povolen přístup na základě identity tohoto kódu: kde pochází z, zda obsahuje [sestavení se silným názvem](../../standard/assembly/strong-named.md), zda je podepsán certifikátem a tak dále.

Technologie ClickOnce, kterou používáte k nasazení aplikací model Windows Forms, vám pomůže usnadnit vývoj aplikací, které běží v částečném vztahu důvěryhodnosti, v úplném vztahu důvěryhodnosti nebo v částečném vztahu důvěryhodnosti se zvýšenými oprávněními. ClickOnce poskytuje funkce, jako je zvýšení oprávnění a nasazení důvěryhodné aplikace, takže vaše aplikace může podle svého zodpovědného vztahu požádat o úplné nebo vyšší oprávnění od místního uživatele.

## <a name="understanding-security-in-the-net-framework"></a>Principy zabezpečení v .NET Framework

Zabezpečení přístupu kódu umožňuje kódu důvěřovat různým stupňům v závislosti na tom, kde kód pochází a na dalších aspektech identity kódu. Další informace o důkazech, které modul CLR (Common Language Runtime) používá k určení zásad zabezpečení, najdete v tématu [legitimace](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7y5x1hcd(v=vs.100)). Pomáhá chránit počítačové systémy před škodlivým kódem a pomáhá chránit důvěryhodný kód před úmyslně nebo omylem ohrozit zabezpečení. Zabezpečení přístupu kódu vám taky poskytuje větší kontrolu nad akcemi, které vaše aplikace může provádět, protože můžete zadat jenom ta oprávnění, která vaše aplikace potřebuje. Zabezpečení přístupu kódu ovlivňuje veškerý spravovaný kód, který cílí na modul CLR (Common Language Runtime), a to i v případě, že tento kód neprovádí jednu kontrolu oprávnění zabezpečení přístupu kódu. Další informace o zabezpečení v .NET Framework najdete v tématech [klíčové koncepty zabezpečení](../../standard/security/key-security-concepts.md) a [Základy zabezpečení přístupu kódu](../misc/code-access-security-basics.md).

Pokud uživatel spustí model Windows Forms spustitelný soubor přímo z webového serveru nebo sdílené složky, bude stupeň důvěryhodnosti udělený vaší aplikaci závislý na tom, kde se nachází kód, a způsobu jeho spuštění. Při spuštění aplikace se automaticky vyhodnotí a obdrží pojmenovanou sadu oprávnění z modulu CLR (Common Language Runtime). Ve výchozím nastavení je kódu z místního počítače udělená úplná sada oprávnění důvěryhodnosti, kód z místní sítě má udělenou sadu oprávnění místního intranetu a kód z Internetu je udělený pro internetovou sadu oprávnění.

> [!NOTE]
> V .NET Framework verze 1,0 Service Pack 1 a Service Pack 2 obdrží skupina kódu Internet Zone sadu oprávnění Nothing. Ve všech ostatních verzích .NET Framework obdrží skupina kódu Internet Zone nastavené oprávnění pro Internet.
>
> Výchozí oprávnění udělená v každé z těchto sad oprávnění jsou uvedená v tématu [výchozí zásady zabezpečení](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/03kwzyfc(v=vs.100)) . V závislosti na oprávněních, která aplikace obdrží, buď funguje správně, nebo vygeneruje výjimku zabezpečení.
>
> Mnohé model Windows Forms aplikace budou nasazeny pomocí technologie ClickOnce. Nástroje používané pro generování nasazení ClickOnce mají jiné výchozí hodnoty zabezpečení než dříve popsané v předchozích krocích. Další informace najdete v následující diskuzi.

Skutečná oprávnění udělená vaší aplikaci můžou být odlišná od výchozích hodnot, protože zásady zabezpečení je možné upravit. To znamená, že vaše aplikace může mít oprávnění na jednom počítači, ale ne na jiném.

## <a name="developing-a-more-secure-windows-forms-application"></a>Vývoj bezpečnější aplikace model Windows Forms

Zabezpečení je důležité ve všech krocích vývoje aplikací. Začněte kontrolou a podle pokynů pro [zabezpečené kódování](../../standard/security/secure-coding-guidelines.md).

Dále rozhodněte, zda aplikace musí běžet v úplném vztahu důvěryhodnosti nebo zda má běžet v částečném vztahu důvěryhodnosti. Spuštění aplikace v úplném vztahu důvěryhodnosti usnadňuje přístup k prostředkům v místním počítači, ale zpřístupňuje vaší aplikaci a jejím uživatelům vysokou bezpečnostní rizika, pokud nebudete navrhovat a vyvíjet aplikaci výhradně v souladu s pokyny pro zabezpečené kódování. výklad. Spuštění aplikace v částečném vztahu důvěryhodnosti usnadňuje vývoj bezpečnější aplikace a snižuje množství rizika, ale vyžaduje více plánování pro implementaci určitých funkcí.

Pokud zvolíte možnost částečná důvěryhodnost (tj. buď sady oprávnění Internet nebo místní intranet), rozhodněte se, jak se má aplikace chovat v tomto prostředí. Model Windows Forms poskytuje alternativní a bezpečnější způsoby implementace funkcí v případě částečně důvěryhodného prostředí. Některé části vaší aplikace, jako je například přístup k datům, lze navrhovat a zapisovat odlišně pro prostředí s částečným i úplným vztahem důvěryhodnosti. Některé funkce model Windows Forms, jako je nastavení aplikace, jsou navržené tak, aby fungovaly v částečném vztahu důvěryhodnosti. Další informace najdete v tématu [Přehled nastavení aplikace](./advanced/application-settings-overview.md).

Pokud vaše aplikace potřebuje více oprávnění, než umožňuje částečná důvěryhodnost, ale nechcete spouštět v úplném vztahu důvěryhodnosti, můžete spustit v částečném vztahu důvěryhodnosti a vyhodnotit jenom ta další oprávnění, která potřebujete. Například pokud chcete spustit v částečném vztahu důvěryhodnosti, ale musíte aplikaci udělit přístup jen pro čtení k adresáři v systému souborů uživatele, můžete požadovat <xref:System.Security.Permissions.FileIOPermission> pouze pro tento adresář. Pomocí tohoto přístupu můžou vaše aplikace zvyšovat funkčnost a minimalizovat rizika zabezpečení pro vaše uživatele.

Když vyvíjíte aplikaci, která se spustí v částečném vztahu důvěryhodnosti, udržujte si přehled o tom, jaká oprávnění vaše aplikace musí spouštět a jaká oprávnění může vaše aplikace volitelně použít. Pokud jsou všechna oprávnění známa, měli byste vytvořit deklarativní požadavek na oprávnění na úrovni aplikace. Žádost o oprávnění informuje .NET Framework dobu běhu o tom, která oprávnění vaše aplikace potřebuje a jaká oprávnění výslovně nechce. Další informace o vyžádání oprávnění najdete v tématu [vyžádání oprávnění](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/yd267cce(v=vs.100)).

Když vyžádáte volitelná oprávnění, musíte zpracovat výjimky zabezpečení, které se vygenerují, pokud vaše aplikace provede akci, která vyžaduje, aby k ní nebyla udělená oprávnění. Vhodným zpracováním <xref:System.Security.SecurityException> se zajistí, že vaše aplikace bude moci i nadále fungovat. Vaše aplikace může výjimku použít k určení, zda má být funkce pro uživatele zakázána. Například aplikace může zakázat možnost nabídky **Uložit** , pokud není uděleno požadované oprávnění souboru.

V některých případech je obtížné zjistit, zda jste vystavili všechna příslušná oprávnění. Volání metody, které vypadá neškodného na povrchu, může například v určitém okamžiku během jejího provádění získat přístup k systému souborů. Pokud neprovedete nasazení aplikace se všemi požadovanými oprávněními, může testování fungovat při ladění na ploše, ale při nasazení dojde k chybě. .NET Framework 2,0 SDK i sada Visual Studio 2005 obsahují nástroje pro výpočet oprávnění, která aplikace potřebuje: nástroj příkazového řádku MT. exe a funkce vypočítat oprávnění v sadě Visual Studio, v uvedeném pořadí.

Následující témata popisují další model Windows Forms funkce zabezpečení.

|Téma|Popis|
|-----------|-----------------|
|- bezpečnější [přístup k souborům a datům v model Windows Forms](more-secure-file-and-data-access-in-windows-forms.md)|Popisuje, jak získat přístup k souborům a datům v prostředí s částečným vztahem důvěryhodnosti.|
|- bezpečnější [Tisk v model Windows Forms](more-secure-printing-in-windows-forms.md)|Popisuje, jak získat přístup k funkcím tisku v prostředí s částečným vztahem důvěryhodnosti.|
|- [Další bezpečnostní opatření v model Windows Forms](additional-security-considerations-in-windows-forms.md)|Popisuje provádění manipulace s oknem, použití schránky a volání nespravovaného kódu v prostředí s částečným vztahem důvěryhodnosti.|

### <a name="deploying-an-application-with-the-appropriate-permissions"></a>Nasazení aplikace s příslušnými oprávněními

Nejběžnějším způsobem nasazení aplikace model Windows Forms do klientského počítače je technologie ClickOnce, která popisuje všechny součásti, které vaše aplikace potřebuje ke spuštění. ClickOnce používá soubory XML označované jako manifesty k popisu sestavení a souborů, které tvoří vaši aplikaci, a také oprávnění, která vaše aplikace vyžaduje.

ClickOnce má dvě technologie pro vyžadování zvýšených oprávnění na klientském počítači. Obě technologie spoléhají na použití certifikátů technologie Authenticode. Certifikáty vám pomůžou zajistit určitou jistotu pro uživatele, že aplikace pochází z důvěryhodného zdroje.

Tyto technologie jsou popsány v následující tabulce.

|Technologie zvýšeného oprávnění|Popis|
|------------------------------------|-----------------|
|Zvýšení oprávnění|Vyzve uživatele k zadání dialogového okna zabezpečení při prvním spuštění aplikace. Dialogové okno **zvýšení úrovně oprávnění** informuje uživatele o tom, kdo aplikaci publikoval, aby si mohl uživatel rozhodnout o tom, jestli má udělit další vztah důvěryhodnosti.|
|Nasazení důvěryhodné aplikace|Vyžaduje, aby správce systému prováděl jednorázovou instalaci certifikátu Authenticode vydavatele na klientském počítači. Od tohoto okamžiku se všechny aplikace podepsané certifikátem považují za důvěryhodné a můžou běžet v úplném vztahu důvěryhodnosti na místním počítači bez dalších výzev.|

Jakou technologii zvolíte, bude záviset na vašem prostředí nasazení. Další informace najdete v tématu [Výběr strategie nasazení ClickOnce](/visualstudio/deployment/choosing-a-clickonce-deployment-strategy).

Ve výchozím nastavení jsou aplikace ClickOnce nasazené pomocí sady Visual Studio nebo nástrojů .NET Framework SDK (Mage. exe a MageUI. exe) nakonfigurované tak, aby běžely v klientském počítači s úplným vztahem důvěryhodnosti. Pokud nasazujete aplikaci pomocí částečné důvěryhodnosti nebo pomocí pouze některých dodatečných oprávnění, bude nutné změnit toto výchozí nastavení. To lze provést buď pomocí sady Visual Studio, nebo nástroje .NET Framework SDK nástroje MageUI. exe při konfiguraci nasazení. Další informace o použití nástroje MageUI. exe naleznete v tématu [Návod: Ruční nasazení aplikace ClickOnce](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-application).  Viz také [Postupy: nastavení vlastních oprávnění pro aplikaci ClickOnce](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2012/hafybdaa(v=vs.110)) nebo [Postup: nastavení vlastních oprávnění pro aplikaci ClickOnce](/visualstudio/deployment/how-to-set-custom-permissions-for-a-clickonce-application).

Další informace o aspektech zabezpečení ClickOnce a zvýšení oprávnění naleznete v tématu [zabezpečení aplikací ClickOnce](/visualstudio/deployment/securing-clickonce-applications). Další informace o nasazení důvěryhodných aplikací naleznete v tématu [Přehled nasazení důvěryhodných aplikací](/visualstudio/deployment/trusted-application-deployment-overview).

### <a name="testing-the-application"></a>Testování aplikace

Pokud jste nasadili aplikaci model Windows Forms pomocí sady Visual Studio, můžete povolit ladění v částečném vztahu důvěryhodnosti nebo v sadě s omezeným oprávněním z vývojového prostředí.  Viz také [Postupy: ladění aplikace ClickOnce s omezenými oprávněními](/visualstudio/deployment/how-to-debug-a-clickonce-application-with-restricted-permissions).

## <a name="see-also"></a>Viz také:

- [Windows Forms – zabezpečení](windows-forms-security.md)
- [Základy zabezpečení přístupu ke kódu](../misc/code-access-security-basics.md)
- [ClickOnce – zabezpečení a nasazení](/visualstudio/deployment/clickonce-security-and-deployment)
- [Přehled nasazení důvěryhodných aplikací](/visualstudio/deployment/trusted-application-deployment-overview)
- [Mage.exe (Manifest Generation and Editing Tool)](../tools/mage-exe-manifest-generation-and-editing-tool.md)
- [MageUI.exe (Manifest Generation and Editing Tool, grafický klient)](../tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client.md)
