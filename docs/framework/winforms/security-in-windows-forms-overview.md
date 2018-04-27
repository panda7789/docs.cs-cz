---
title: Přehled zabezpečení ve Windows Forms
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- code access security [Windows Forms], Windows Forms
- permissions [Windows Forms], Windows Forms
- Windows Forms, security
- security [Windows Forms], about security
- access control [Windows Forms], Windows Forms
ms.assetid: 4810dc9f-ea23-4ce1-8ea1-657f0ff1d820
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 57f46620e7b98bb1a4c120684075dbe065db9714
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2018
---
# <a name="security-in-windows-forms-overview"></a>Přehled zabezpečení ve Windows Forms
Před vydáním [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], všechny kód spuštěný na uživatele je počítač měl stejné práva nebo oprávnění k přístupu k prostředkům měl uživatel počítače. Například pokud uživatel byl povolen přístup k systému souborů, kód byl povolen přístup systému souborů. Uživatel byl povolen přístup k databázi, kód byl povolen přístup k databázi. I když tato práva nebo oprávnění může být přijatelné pro kód ve spustitelné soubory, které uživatel nainstaloval explicitně v místním počítači, se nemusí být přijatelné pro potenciálně škodlivého kódu, pocházejících z Internetu nebo intranetu. Tento kód by neměly mít přístup k prostředkům počítače uživatele bez oprávnění.  
  
 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Zavádí infrastruktury názvem zabezpečení přístupu kódu, který umožňuje rozlišit oprávnění nebo práva, které má kód z práv, která má uživatel. Ve výchozím kódu pocházejících z Internetu a intranetu spustit pouze v, která se označuje jako částečné důvěryhodnosti. Částečná důvěryhodnost předměty aplikace na řadu omezení: mimo jiné aplikace je omezení přístupu k místním pevném disku a nelze spustit nespravovaného kódu. [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Určuje prostředky, které kód je povolen přístup na základě identity tento kód: kde pochází z, zda má [sestavení se silným názvem](../../../docs/framework/app-domains/strong-named-assemblies.md), zda je podepsaný certifikát, a tak dále.  
  
 [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] technologie, které můžete použít k nasazení aplikace Windows Forms, pomáhá usnadnit práci pro vývoj aplikací, které běží v částečné důvěryhodnosti, v režimu plné důvěryhodnosti nebo v částečné důvěryhodnosti se zvýšenými oprávněními. [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] poskytuje funkce, jako je zvýšení úrovně oprávnění a nasazení důvěryhodných aplikací tak, aby vaše aplikace může požadovat úplný vztah důvěryhodnosti nebo zvýšenými oprávněními z místního uživatele zodpovědně.  
  
## <a name="understanding-security-in-the-net-framework"></a>Principy zabezpečení v rozhraní .NET Framework  
 Zabezpečení přístupu kódu umožňuje kódu být důvěryhodný na různých úrovních, v závislosti na tom, odkud pochází kód a na dalších aspektů identity kódu. Další informace o důkazy modul common language runtime používá k určení zásady zabezpečení najdete v tématu [důkaz](http://msdn.microsoft.com/library/64ceb7c8-a0b4-46c4-97dc-6c22da0539da). Pomáhá chránit systémy počítače z škodlivý kód a pomáhá chránit důvěryhodný kód z záměrně nebo neúmyslně ohrožení zabezpečení. Zabezpečení přístupu kódu také vám dává větší kontrolu nad jaké akce aplikace můžete provést, protože lze zadat pouze oprávnění, je nutné, aby vaše aplikace měla. Zabezpečení přístupu kódu ovlivňuje všechny spravovaného kódu, který cílí modul common language runtime i v případě, že tento kód neobsahuje zkontrolujte jednom – zabezpečení přístupu kódu – kontrola oprávnění. Další informace o zabezpečení v [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], najdete v části [klíčové koncepty zabezpečení](../../../docs/standard/security/key-security-concepts.md) a [Základy zabezpečení přístupu kódu](../../../docs/framework/misc/code-access-security-basics.md).  
  
 Pokud uživatel spustit spustitelný soubor Windows Forms přímo z webového serveru nebo sdílené složky, stupeň důvěryhodnosti udělit aplikaci závisí na níž se nachází kód a jeho spuštění. Když aplikace běží, je automaticky vyhodnotit a obdrží pojmenovanou sadu oprávnění z modulu CLR. Ve výchozím nastavení, kód z místního počítače je uděleno oprávnění k úplné důvěryhodnosti nastavíte, kód z místní sítě je uděleno oprávnění sady místní Intranet a kód z Internetu jsou udělena oprávnění sadu Internet.  
  
> [!NOTE]
>  V [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] verze 1.0 Service Pack 1 a Service Pack 2, Internetu zónu skupiny kódu obdrží žádnou sadu oprávnění. V jiných verzích [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], skupiny kódu zónu Internetu obdrží internetové sady oprávnění.  
>   
>  Výchozí oprávnění udělená v každé z těchto sad oprávnění jsou uvedeny v [výchozí zásady zabezpečení](http://msdn.microsoft.com/library/2c086873-0894-4f4d-8f7e-47427c1a3b55) tématu. V závislosti na oprávnění, která obdrží aplikace je buď běží správně, nebo vygeneruje výjimka zabezpečení.  
>   
>  Mnoho aplikací Windows Forms se nasadí pomocí [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)]. Nástroje používané ke generování [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] nasazení mají výchozí hodnoty různých zabezpečení než co byl uvedenými výše. Další informace najdete v tématu následující diskusi.  
  
 Skutečná oprávnění udělená aplikaci může být jiný než výchozí hodnoty, protože zásady zabezpečení můžete upravovat; To znamená, že vaše aplikace může mít oprávnění na jednom počítači, ale ne na jiném.  
  
## <a name="developing-a-more-secure-windows-forms-application"></a>Vývoj bezpečnější aplikace Windows Forms  
 Zabezpečení je důležité pro všechny kroky pro vývoj aplikací. Spuštění kontroly a následující [pokyny zabezpečení kódování](../../../docs/standard/security/secure-coding-guidelines.md).  
  
 V dalším kroku rozhodněte, jestli vaše aplikace musíte spustit v režimu plné důvěryhodnosti, nebo jestli se má spustit v částečné důvěryhodnosti. Spuštění aplikace v režimu plné důvěryhodnosti usnadňuje přístup k prostředkům v místním počítači, ale zveřejňuje vaší aplikace a její uživatele na vysoké bezpečnostní rizika, pokud nemáte návrh a vývoj aplikace výhradně podle pokynů zabezpečené kódování téma. Spuštění aplikace v částečné důvěryhodnosti usnadňuje vývoj bezpečnější aplikace a snižuje riziko, mnoho, ale vyžaduje další plánování v tom, jak implementovat určité funkce.  
  
 Pokud si zvolíte částečné důvěryhodnosti (který je buď Internetu nebo místní Intranet sady oprávnění), rozhodněte, jak má vaše aplikace se bude chovat, v tomto prostředí. Windows Forms poskytuje bezpečnější, alternativní způsoby, jak implementovat funkce v prostředí s polovičním důvěryhodné. Některé částí aplikace, jako je přístup k datům, můžete určené a zapsány odlišně pro úplný vztah důvěryhodnosti v prostředích a částečné důvěryhodnosti. Některé funkce Windows Forms, jako je nastavení aplikace, jsou navrženy pro práci v částečné důvěryhodnosti. Další informace najdete v tématu [přehled nastavení aplikace](../../../docs/framework/winforms/advanced/application-settings-overview.md).  
  
 Pokud aplikace potřebuje více oprávnění, než umožňuje částečné důvěryhodnosti, ale nechcete spustit v režimu plné důvěryhodnosti, můžete spustit v částečné důvěryhodnosti a potvrzující pouze další oprávnění, které potřebujete. Například pokud chcete spustit v částečné důvěryhodnosti, ale musí udělit aplikaci jen pro čtení přístup do adresáře v systému souborů uživatele, můžete požádat <xref:System.Security.Permissions.FileIOPermission> pouze pro tento adresář. Při správném použití tento přístup udělit funkčnost aplikace vyšší a minimalizace rizika zabezpečení pro vaše uživatele.  
  
 Při vývoji aplikace, která se spustí v částečné důvěryhodnosti sledovat uvedete, jaká oprávnění aplikace musíte spustit a uvedete, jaká oprávnění vaše aplikace může volitelně používat. Když se ví, že všechna oprávnění, měl by deklarativní žádost o oprávnění na úrovni aplikace. Požaduje oprávnění informuje [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] běh o oprávnění, která vaše aplikace potřebuje, a oprávnění, která ji výslovně nechce. Další informace o vyžadování oprávnění najdete v tématu [požaduje oprávnění](http://msdn.microsoft.com/library/0447c49d-8cba-45e4-862c-ff0b59bebdc2).  
  
 Pokud budete požadovat volitelné oprávnění, je nutné zajistit zabezpečení výjimky, které budou generovány, pokud vaše aplikace provede akci, která vyžaduje oprávnění nejsou udělena na ni. Odpovídající zpracování <xref:System.Security.SecurityException> zajistí, že vaše aplikace bude pracovat. Aplikace můžete použít výjimku pro určete, zda funkce by měl být zakázán pro uživatele. Například můžete zakázat aplikaci **Uložit** nabídky možnost, pokud není udělit oprávnění k požadovaný soubor.  
  
 V některých případech je obtížné zjistit, pokud mají prohlašovanou příslušná oprávnění. Volání metody, která vypadá neškodné na povrchu, třeba, může získat přístup k systému souborů v určitém okamžiku během jejího provádění. Pokud neprovedete nasazení aplikace s požadovanými oprávněními, se může testovat bez problémů při ladění na pracovní ploše, ale selhání při nasazení. Obě [!INCLUDE[dnprdnlong](../../../includes/dnprdnlong-md.md)] SDK a [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] obsahovat nástroje pro výpočet oprávnění aplikace potřebuje: příkaz MT.exe nástroj řádku a funkci výpočtu oprávnění sady Visual Studio, v uvedeném pořadí.  
  
 Následující témata popisují další funkce zabezpečení Windows Forms.  
  
|Téma|Popis|  
|-----------|-----------------|  
|-   [Bezpečnější souborové služby a přístup k datům ve Windows Forms](../../../docs/framework/winforms/more-secure-file-and-data-access-in-windows-forms.md)|Popisuje, jak přístup k souborům a data v prostředí s částečnou důvěryhodností.|  
|-   [Bezpečnější tisk ve Windows Forms](../../../docs/framework/winforms/more-secure-printing-in-windows-forms.md)|Popisuje, jak chcete dostat ke službám tisku v prostředí s částečnou důvěryhodností.|  
|-   [Dodatečné informace o zabezpečení ve Windows Forms](../../../docs/framework/winforms/additional-security-considerations-in-windows-forms.md)|Popisuje provádění okno manipulaci, použití schránky a volání nespravovaného kódu v prostředí s částečnou důvěryhodností.|  
  
-  
  
### <a name="deploying-an-application-with-the-appropriate-permissions"></a>Nasazení aplikace s příslušnými oprávněními.  
 Nejběžnější způsob nasazení aplikace Windows Forms ke klientskému počítači je s [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)], nasazení technologie, která popisuje všechny součásti aplikace je potřeba spustit. [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] soubory XML používá nazývá manifesty popis sestavení a soubory, které tvoří vaši aplikaci a taky oprávnění vaše aplikace vyžaduje.  
  
 [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] má dvě technologie pro požadování zvýšenými oprávněními na klientském počítači. Obě technologie spoléhají na použití certifikátů Authenticode. Certifikáty pomáhají zajistit některé záruku svým uživatelům, které aplikace pochází z důvěryhodného zdroje.  
  
 Následující tabulka popisuje tyto technologie.  
  
|Zvýšená oprávnění technologie|Popis|  
|------------------------------------|-----------------|  
|Zvýšení úrovně oprávnění|Vyzve uživatele s časem při prvním dialogové okno zabezpečení vaše aplikace běží. **Zvýšení úrovně oprávnění** dialogové okno informuje uživatele, o který publikovat aplikaci, tak, aby uživatel může provést informované rozhodnutí o tom, jestli ho udělit další vztah důvěryhodnosti|  
|Nasazení důvěryhodné aplikace|Zahrnuje správce systému provádění jednorázovou instalaci certifikátu vydavatele Authenticode na klientském počítači. Od tohoto okamžiku se považuje za všechny aplikace podepsané certifikátem jako důvěryhodné a můžete spustit na úplný vztah důvěryhodnosti v místním počítači bez další výzvy.|  
  
 Technologii, kterou zvolíte, bude záviset na prostředí pro nasazení. Další informace najdete v tématu [Výběr strategie nasazení ClickOnce](/visualstudio/deployment/choosing-a-clickonce-deployment-strategy).  
  
 Ve výchozím nastavení [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] aplikace nasazené pomocí buď sady Visual Studio nebo [!INCLUDE[dnprdnlong](../../../includes/dnprdnlong-md.md)] SDK tools (Mage.exe a MageUI.exe) jsou nakonfigurovány na spuštění v klientském počítači, který má úplný vztah důvěryhodnosti. Pokud nasazujete aplikaci s použitím částečné důvěryhodnosti nebo pomocí jenom některé další oprávnění, bude třeba změnit toto výchozí nastavení. To lze provést pomocí buď Visual Studio nebo [!INCLUDE[dnprdnlong](../../../includes/dnprdnlong-md.md)] nástroj sady SDK MageUI.exe při konfiguraci vašeho nasazení. Další informace o tom, jak používat MageUI.exe najdete v tématu Návod: nasazení aplikace ClickOnce z příkazového řádku.  Viz také [postup: nastavit vlastní oprávnění pro aplikaci ClickOnce](http://msdn.microsoft.com/library/hafybdaa\(v=vs.110\)) nebo [postup: nastavit vlastní oprávnění pro aplikaci ClickOnce](http://msdn.microsoft.com/library/hafybdaa\(v=vs.120\)).  
  
 Další informace o aspektech zabezpečení [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] a zvýšení úrovně oprávnění, najdete v části [zabezpečení aplikací ClickOnce](/visualstudio/deployment/securing-clickonce-applications). Další informace o nasazení důvěryhodných aplikací najdete v tématu [Přehled nasazení důvěryhodných aplikací](/visualstudio/deployment/trusted-application-deployment-overview).  
  
### <a name="testing-the-application"></a>Testování aplikace  
 Pokud jste nasadili aplikace Windows Forms pomocí sady Visual Studio, můžete povolit ladění v částečné důvěryhodnosti nebo s omezenými oprávněními nastavit z vývojového prostředí.  Viz také [postupy: ladění aplikace ClickOnce s omezenými oprávněními](http://msdn.microsoft.com/library/593zkfdf\(v=vs.110\)) nebo [postupy: ladění aplikace ClickOnce s omezenými oprávněními](http://msdn.microsoft.com/library/593zkfdf\(v=vs.120\)).  
  
## <a name="see-also"></a>Viz také  
 [Windows Forms – zabezpečení](../../../docs/framework/winforms/windows-forms-security.md)  
 [Základy zabezpečení přístupu kódu](../../../docs/framework/misc/code-access-security-basics.md)  
 [ClickOnce – zabezpečení a nasazení](/visualstudio/deployment/clickonce-security-and-deployment)  
 [Přehled nasazení důvěryhodných aplikací](/visualstudio/deployment/trusted-application-deployment-overview)  
 [Mage.exe (Manifest Generation and Editing Tool)](../../../docs/framework/tools/mage-exe-manifest-generation-and-editing-tool.md)  
 [MageUI.exe (Manifest Generation and Editing Tool, grafický klient)](../../../docs/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client.md)
