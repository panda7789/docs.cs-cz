---
title: Přehled zabezpečení ve Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- code access security [Windows Forms], Windows Forms
- permissions [Windows Forms], Windows Forms
- Windows Forms, security
- security [Windows Forms], about security
- access control [Windows Forms], Windows Forms
ms.assetid: 4810dc9f-ea23-4ce1-8ea1-657f0ff1d820
ms.openlocfilehash: 54fc56e5e7d6ee5cd0e7bc55bd22c7d4127eb4d3
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43532115"
---
# <a name="security-in-windows-forms-overview"></a>Přehled zabezpečení ve Windows Forms
Před vydáním [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], všechny kód spuštěný na uživatele v počítači měl stejné práva nebo oprávnění pro přístup k prostředkům, které měl uživatel počítače. Například pokud byl uživatel pro přístup k systému souborů, kód byl povolen přístup k systému souborů. Uživatel byl povolen přístup k databázi, kód byl povolen přístup k této databázi. Ačkoli tato práva nebo oprávnění může být přijatelný pro kód v spustitelné soubory, které uživatel nainstaloval explicitně v místním počítači, se nemusí být přijatelné pro potenciálně škodlivý kód pocházející z Internetu nebo intranetu. Tento kód by neměl být přístup k prostředkům počítače uživatele bez oprávnění.  
  
 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Zavádí infrastrukturu volá zabezpečení přístupu kódu, který umožňuje rozlišit oprávnění nebo práva, která má kód ze práva, která má uživatel. Ve výchozím nastavení můžete spustit v jaké se označuje jako částečné důvěryhodnosti pouze kód pocházející z Internetu a intranetu. Aplikace pro řadu omezení Predmety částečným vztahem důvěryhodnosti: mimo jiné aplikace je omezen přístup na místní pevný disk a nespravovaný kód nelze spustit. [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Určuje prostředky, které kód je povolen přístup na základě identity, že kód: kdy a odkud, zda má [sestavení se silným názvem](../../../docs/framework/app-domains/strong-named-assemblies.md), ať už je podepsaný certifikát, a tak dále.  
  
 [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] technologie, které můžete použít k nasazení aplikace Windows Forms, pomáhá zjednodušit vývoj aplikací, které běží v částečném vztahu důvěryhodnosti, v režimu plné důvěryhodnosti nebo v částečném vztahu důvěryhodnosti se zvýšenými oprávněními. [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] poskytuje funkce, jako je zvýšení úrovně oprávnění a nasazení důvěryhodné aplikace tak, aby vaše aplikace může požadovat úplný vztah důvěryhodnosti nebo zvýšenou úroveň oprávnění z místního uživatele zodpovědně.  
  
## <a name="understanding-security-in-the-net-framework"></a>Principy zabezpečení v rozhraní .NET Framework  
 Zabezpečení přístupu kódu umožňuje kódu důvěryhodné na různých úrovních, v závislosti na tom, odkud pochází kód a o dalších aspektech identity kódu. Další informace o legitimaci modul common language runtime používá k určení zásady zabezpečení, najdete v části [důkazy](https://msdn.microsoft.com/library/64ceb7c8-a0b4-46c4-97dc-6c22da0539da). Pomáhá chránit před škodlivým kódem počítačových systémů a pomáhá chránit důvěryhodného kódu z úmyslně nebo neúmyslně tím bylo narušeno zabezpečení. Zabezpečení přístupu kódu také poskytuje větší kontrolu nad jaké akce lze provádět vaší aplikace, protože můžete určit pouze oprávnění, je nutné mít vaše aplikace. Zabezpečení přístupu kódu má vliv na všechny spravovaný kód, který se zaměřuje na modul common language runtime, i v případě, že kód nemá značku jednoho – zabezpečení přístupu kódu – kontrola oprávnění. Další informace o zabezpečení [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], naleznete v tématu [klíčové koncepty zabezpečení](../../../docs/standard/security/key-security-concepts.md) a [Základy zabezpečení přístupu kódu](../../../docs/framework/misc/code-access-security-basics.md).  
  
 Pokud uživatel spustit spustitelný soubor Windows Forms přímo z webového serveru nebo sdílené složky, stupeň důvěryhodnosti udělena pro vaše aplikace závisí na ve které se nachází kódu a jak je spuštěno. Pokud je aplikace spuštěna, automaticky se vyhodnotí a přijímá pojmenovanou sadu oprávnění ze modul common language runtime. Ve výchozím kódu z místního počítače je uděleno oprávnění plné důvěryhodnosti nastavíte, kód z místní sítě je udělena sada oprávnění místního intranetu a kód z Internetu je udělena sada oprávnění Internetu.  
  
> [!NOTE]
>  V [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Nothing obdrží verze 1.0 Service Pack 1 a Service Pack 2, Internetu zóna kódová skupina sadu oprávnění. V jiných verzích [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], obdrží kódová skupina zóny Internetu sadu oprávnění sítě Internet.  
>   
>  Výchozí oprávnění udělené v každé z těchto sad oprávnění jsou uvedeny v [výchozí zásady zabezpečení](https://msdn.microsoft.com/library/2c086873-0894-4f4d-8f7e-47427c1a3b55) tématu. V závislosti na oprávněních, které aplikace obdrží je buď běží správně nebo vygeneruje výjimka zabezpečení.  
>   
>  Mnoho aplikací Windows Forms bude možné nasadit s použitím [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)]. Nástroje pro generování [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] nasazení mají výchozí hodnoty zabezpečení, než co byl popsán výše. Další informace najdete v tématu následující diskuse.  
  
 Skutečná oprávnění udělená aplikaci může lišit od výchozí hodnoty, protože zásady zabezpečení lze upravovat. To znamená, že vaše aplikace může mít oprávnění v jednom počítači, ale v jiné ne.  
  
## <a name="developing-a-more-secure-windows-forms-application"></a>Vývoj bezpečnější aplikace Windows Forms  
 Zabezpečení je důležité ve všech fázích vývoje aplikací. Začněte tím, že zkontrolujete a postupovat [zabezpečené kódování zásady](../../../docs/standard/security/secure-coding-guidelines.md).  
  
 Dále rozhodněte, jestli musíte spustit aplikaci v režimu plné důvěryhodnosti, nebo jestli se má spustit v částečném vztahu důvěryhodnosti. Spuštění aplikace v režimu plné důvěryhodnosti usnadňuje přístup k prostředkům v místním počítači, ale zveřejňuje vaší aplikace a její uživatele na vysoké bezpečnostní rizika, pokud není navrhovat a vyvíjet aplikace výhradně podle pokynů zabezpečené kódování téma. Spuštění aplikace v částečném vztahu důvěryhodnosti usnadňuje vývoj bezpečnější aplikace a snižuje množství riziko, ale vyžaduje více plánování v tom, jak implementovat určité funkce.  
  
 Pokud se rozhodnete částečné důvěryhodnosti (to znamená, buď Internetu a místního intranetu sady oprávnění), rozhodněte, jak chcete, aby vaše aplikace chovat v tomto prostředí. Windows Forms poskytuje alternativní bezpečnější metody k implementaci funkcí v částečně důvěryhodném prostředí. Některé části vaší aplikace, jako je například přístup k datům, můžete navržené a jinak napsané pro prostředí úplný vztah důvěryhodnosti a částečný vztah důvěryhodnosti. Některé funkce Windows Forms, jako je například nastavení aplikace, jsou navrženy pro práci v částečném vztahu důvěryhodnosti. Další informace najdete v tématu [přehled nastavení aplikace](../../../docs/framework/winforms/advanced/application-settings-overview.md).  
  
 Pokud vaše aplikace potřebuje více oprávnění než umožňuje částečným vztahem důvěryhodnosti, ale nechcete spustit v úplném vztahu důvěryhodnosti, můžete spustit v částečném vztahu důvěryhodnosti při uplatnění pouze další oprávnění, které potřebujete. Například pokud chcete spustit v částečném vztahu důvěryhodnosti, ale musí udělit vaší aplikace do adresáře na uživatele systému souborů přístup jen pro čtení, můžete požádat o <xref:System.Security.Permissions.FileIOPermission> pouze pro tento adresář. Správně použity, tento přístup udělit funkčnost aplikace, která zvýšil a minimalizovat rizika zabezpečení pro vaše uživatele.  
  
 Když vyvíjíte aplikaci, která se spustí v částečném vztahu důvěryhodnosti, sledovat, jaká oprávnění, musíte spustit aplikaci a jaká oprávnění aplikace může volitelně používat. Když jsou všechna oprávnění, která označuje, měli byste zajistit deklarativní žádost o oprávnění na úrovni aplikace. Požaduje oprávnění informuje [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] běhu o oprávnění, která vaše aplikace potřebuje a oprávnění, která je speciálně nechce. Další informace o oprávnění najdete v tématu [požaduje oprávnění](https://msdn.microsoft.com/library/0447c49d-8cba-45e4-862c-ff0b59bebdc2).  
  
 Pokud budete požadovat volitelné oprávnění, musí zpracovat výjimky zabezpečení, které budou generovány, pokud aplikace provádí akci, která vyžaduje oprávnění nebyla udělena. Odpovídající zpracování <xref:System.Security.SecurityException> zajistí, že vaše aplikace může i nadále fungovat. Aplikace může výjimku použít k určení, zda by měla funkce deaktivuje pro daného uživatele. Například můžete zakázat aplikaci **Uložit** možnost nabídky, pokud není uděleno oprávnění požadovaný soubor.  
  
 Někdy je těžké vědět, pokud máte s prohlašovanou příslušná oprávnění. Volání metody, která vypadá neškodného na povrchu, například může přístup k systému souborů v určitém okamžiku během jejího provádění. Pokud nezvolíte nasazení aplikace s požadovanými oprávněními, se může otestovat bez problémů při ladění na vašem počítači, ale selhat při nasazení. Oba [!INCLUDE[dnprdnlong](../../../includes/dnprdnlong-md.md)] sady SDK a [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] obsahovat nástroje pro výpočet oprávnění aplikace potřebuje: příkaz MT.exe čára a vlastnost Calculate Permissions sady Visual Studio, v uvedeném pořadí.  
  
 Následující témata popisují další funkce zabezpečení Windows Forms.  
  
|Téma|Popis|  
|-----------|-----------------|  
|-   [Vyšší úroveň zabezpečení souboru a přístup k datům ve Windows Forms](../../../docs/framework/winforms/more-secure-file-and-data-access-in-windows-forms.md)|Popisuje, jak získat přístup k souborům a datům v prostředí s částečnou důvěryhodností.|  
|-   [Bezpečnější tisk ve Windows Forms](../../../docs/framework/winforms/more-secure-printing-in-windows-forms.md)|Popisuje, jak získat přístup k funkcím tisku v prostředí s částečnou důvěryhodností.|  
|-   [Dodatečné informace o zabezpečení ve Windows Forms](../../../docs/framework/winforms/additional-security-considerations-in-windows-forms.md)|Popisuje provádění manipulaci s okna, použití schránky a volání nespravovaného kódu v prostředí s částečnou důvěryhodností.|  
  
-  
  
### <a name="deploying-an-application-with-the-appropriate-permissions"></a>Nasazení aplikace s příslušnými oprávněními  
 Nejběžnější způsob nasazení aplikace Windows Forms ke klientskému počítači je s [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)], technologie nasazení, která popisuje všechny součásti, které vaše aplikace potřebuje ke spuštění. [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] soubory XML používá volá manifesty popisují sestavení a souborů, které tvoří vaši aplikaci a také oprávnění vaše aplikace vyžaduje.  
  
 [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] má dvě technologie pro požadování zvýšenou úroveň oprávnění na klientském počítači. Spolehněte se na používání certifikátů Authenticode obou technologií. Certifikáty pomáhají poskytovat záruku toho některé na uživatele, že aplikace pochází z důvěryhodného zdroje.  
  
 Následující tabulka popisuje tyto technologie.  
  
|Zvýšená oprávnění technologie|Popis|  
|------------------------------------|-----------------|  
|Zvýšení úrovně oprávnění|Se zobrazí výzva s časem zabezpečení dialogového okna při prvním spuštění aplikace. **Zvýšení úrovně oprávnění** dialogové okno informuje uživatele o vydavatele aplikace, tak, aby uživatel mohl provést informované rozhodnutí o tom, jestli jí udělit další důvěryhodnosti|  
|Nasazení důvěryhodné aplikace|Zahrnuje správce systému provádí jednorázové instalaci certifikátu vydavatele Authenticode na klientském počítači. Od tohoto okamžiku na všechny aplikace podepsané certifikátem jsou považovány za důvěryhodné a spustit v úplném vztahu důvěryhodnosti v místním počítači bez dalších výzev.|  
  
 Technologii, kterou zvolíte, závisí na prostředí pro nasazení. Další informace najdete v tématu [Výběr strategie nasazení ClickOnce](/visualstudio/deployment/choosing-a-clickonce-deployment-strategy).  
  
 Ve výchozím nastavení [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] aplikace nasazené pomocí nástroje Visual Studio nebo [!INCLUDE[dnprdnlong](../../../includes/dnprdnlong-md.md)] nástroje sady SDK (Mage.exe a MageUI.exe) jsou nakonfigurovány na spuštění v klientském počítači, který má úplný vztah důvěryhodnosti. Pokud nasazujete aplikaci s použitím částečným vztahem důvěryhodnosti nebo s použitím pouze některá další oprávnění, budete muset změnit toto výchozí nastavení. To lze provést pomocí sady Visual Studio nebo [!INCLUDE[dnprdnlong](../../../includes/dnprdnlong-md.md)] sady SDK nástroje MageUI.exe při konfiguraci vašeho nasazení. Další informace o tom, jak používat MageUI.exe, najdete v článku návod: nasazení aplikace ClickOnce z příkazového řádku.  Viz také [jak: nastavit vlastní oprávnění pro aplikaci ClickOnce](https://msdn.microsoft.com/library/hafybdaa\(v=vs.110\)) nebo [jak: nastavit vlastní oprávnění pro aplikaci ClickOnce](https://msdn.microsoft.com/library/hafybdaa\(v=vs.120\)).  
  
 Další informace o aspektech zabezpečení [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] a zvýšení úrovně oprávnění, najdete v článku [zabezpečení aplikací ClickOnce](/visualstudio/deployment/securing-clickonce-applications). Další informace o nasazení důvěryhodných aplikací najdete v tématu [Trusted Application Deployment Overview](/visualstudio/deployment/trusted-application-deployment-overview).  
  
### <a name="testing-the-application"></a>Testování aplikace  
 Pokud jste nasadili aplikaci Windows Forms pomocí sady Visual Studio, můžete povolit ladění v částečném vztahu důvěryhodnosti nebo sada z vývojového prostředí omezené oprávnění.  Viz také [postupy: ladění aplikace ClickOnce s omezenými oprávněními](https://msdn.microsoft.com/library/593zkfdf\(v=vs.110\)) nebo [postupy: ladění aplikace ClickOnce s omezenými oprávněními](https://msdn.microsoft.com/library/593zkfdf\(v=vs.120\)).  
  
## <a name="see-also"></a>Viz také  
 [Windows Forms – zabezpečení](../../../docs/framework/winforms/windows-forms-security.md)  
 [Základy zabezpečení přístupu kódu](../../../docs/framework/misc/code-access-security-basics.md)  
 [ClickOnce – zabezpečení a nasazení](/visualstudio/deployment/clickonce-security-and-deployment)  
 [Přehled nasazení důvěryhodných aplikací](/visualstudio/deployment/trusted-application-deployment-overview)  
 [Mage.exe (Manifest Generation and Editing Tool)](../../../docs/framework/tools/mage-exe-manifest-generation-and-editing-tool.md)  
 [MageUI.exe (Manifest Generation and Editing Tool, grafický klient)](../../../docs/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client.md)
