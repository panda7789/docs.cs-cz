---
title: Používání knihoven z částečně důvěryhodného kódu
ms.date: 03/30/2017
helpviewer_keywords:
- security [.NET Framework], partially trusted code
- partially trusted code
- partial trust
- AllowPartiallyTrustedCallersAttribute attribute
- code access security, partially trusted code
- APTCA
ms.assetid: dd66cd4c-b087-415f-9c3e-94e3a1835f74
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3b2eaf6ccebed38c778e328e34cb6f53177347b2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33397657"
---
# <a name="using-libraries-from-partially-trusted-code"></a>Používání knihoven z částečně důvěryhodného kódu
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
> [!NOTE]
>  Toto téma řeší chování sestavení se silným názvem a platí jenom pro [úrovně 1](../../../docs/framework/misc/security-transparent-code-level-1.md) sestavení. [Kód transparentní pro zabezpečení, úroveň 2](../../../docs/framework/misc/security-transparent-code-level-2.md) sestavení v [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] nebo později nemá vliv silné názvy. Další informace o změnách systému zabezpečení najdete v tématu [změny zabezpečení](../../../docs/framework/security/security-changes.md).  
  
 Aplikace, které přijímají menší než úplný vztah důvěryhodnosti z jeho hostitele nebo izolovaného prostoru není povoleno volat sdílené spravované knihovny zapisovače knihovny specificky umožňují jim prostřednictvím <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atribut. Autoři aplikace musí být tedy vědět, že některé knihovny nebudete mít k dispozici k nim z částečně důvěryhodného kontextu. Ve výchozím nastavení, všechny kódu, která se spouští v částečné důvěryhodnosti [izolovaného prostoru](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md) a není v seznamu plné důvěryhodnosti sestavení je částečně důvěryhodné. Pokud neočekáváte kódu spouštění z částečně důvěryhodného kontextu nebo má být volána částečně důvěryhodným kódem, nemáte starat o informace v této části. Však můžete psát kód, který musí komunikovat s částečně důvěryhodným kódem nebo pracovat z částečně důvěryhodného kontextu, je třeba zvážit následující faktory:  
  
-   Knihovny musí být podepsané se silným názvem, aby bylo možné sdílet mezi více aplikacemi. Silné názvy povolit kódu být umístěny v globální mezipaměti sestavení nebo přidat do seznamu plné důvěryhodnosti sandboxing <xref:System.AppDomain>, a povolit příjemcům ověřit, že konkrétním mobilního kódu ve skutečnosti pocházejí od vás.  
  
-   Ve výchozím nastavení, silným názvem [úrovně 1](../../../docs/framework/misc/security-transparent-code-level-1.md) sdílené knihovny provést implicitní [LinkDemand](../../../docs/framework/misc/link-demands.md) pro úplné důvěryhodnosti automaticky, aniž by museli něco dělat zapisovač knihovny.  
  
-   Pokud volající nemá úplný vztah důvěryhodnosti, ale pořád se pokouší volat tuto knihovnu, modul runtime vyvolá <xref:System.Security.SecurityException> a volající není povoleno propojení do knihovny.  
  
-   Aby bylo možné zakázat automatické **LinkDemand** a zabránit vyvolání výjimky, můžete umístit **AllowPartiallyTrustedCallersAttribute** atribut na sestavení rozsahu sdílenou Knihovna. Tento atribut umožňuje vašich knihovnách, která se má volat z částečně důvěryhodného spravovaného kódu.  
  
-   Částečně důvěryhodný kód, který je udělen přístup k tomuto atributu do knihovny, je stále podléhá další omezení, které jsou definované <xref:System.AppDomain>.  
  
-   Neexistuje žádný programový způsob pro částečně důvěryhodného kódu pro volání knihovny, který nemá **AllowPartiallyTrustedCallersAttribute** atribut.  
  
 Knihovny, které jsou privátní na konkrétní aplikaci nevyžadují silný název nebo **AllowPartiallyTrustedCallersAttribute** atribut a nemůže být odkazován potenciálně škodlivého kódu, mimo aplikaci. Takový kód je chráněna proti zneužití úmyslnému i neúmyslnému částečně důvěryhodného kódu mobilní bez vývojář si museli dělat žádné další.  
  
 Je třeba zvážit explicitní povolení používání částečně důvěryhodného kódu pro následující typy kódu:  
  
-   Kód, který byl usilovně testován pro chyby zabezpečení a je v souladu se zásadami popsanými v [pokyny zabezpečení kódování](../../../docs/standard/security/secure-coding-guidelines.md).  
  
-   Knihovny kódu se silným názvem, které jsou napsané konkrétně pro částečně důvěryhodné scénáře.  
  
-   Všechny součásti (jestli částečně nebo zcela důvěryhodné) podepsáno silným názvem, který bude volán kódem, který byl stažen z Internetu.  
  
> [!NOTE]
>  Některé třídy v knihovně tříd rozhraní .NET Framework nemají **AllowPartiallyTrustedCallersAttribute** atribut a nedají se volat částečně důvěryhodným kódem.  
  
## <a name="see-also"></a>Viz také  
 [Zabezpečení přístupu kódu](../../../docs/framework/misc/code-access-security.md)
