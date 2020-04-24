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
ms.openlocfilehash: 61291a07639c3f92a05f78dff49f6b20f1aee77e
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645719"
---
# <a name="using-libraries-from-partially-trusted-code"></a>Používání knihoven z částečně důvěryhodného kódu
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
> [!NOTE]
> Toto téma řeší chování sestavení se silným názvem a vztahuje se pouze na sestavení [úrovně 1.](security-transparent-code-level-1.md) [Transparentní kód zabezpečení,](security-transparent-code-level-2.md) sestavení úrovně 2 v rozhraní .NET Framework 4 nebo novější nejsou ovlivněny silnými názvy. Další informace o změnách v systému zabezpečení naleznete v [tématu Změny zabezpečení](https://docs.microsoft.com/previous-versions/dotnet/framework/security/security-changes).  
  
 Aplikace, které obdrží méně než úplný vztah důvěryhodnosti od svého hostitele nebo izolovaného prostoru, nesmějí volat <xref:System.Security.AllowPartiallyTrustedCallersAttribute> sdílené spravované knihovny, pokud jim to zapisovatel knihovny výslovně nepovolí pomocí atributu. Proto je třeba, aby autoři aplikací věděli, že některé knihovny nebudou k dispozici z částečně důvěryhodného kontextu. Ve výchozím nastavení je veškerý kód, který se spouští v [izolovaném prostoru](how-to-run-partially-trusted-code-in-a-sandbox.md) s částečnou důvěryhodností a není v seznamu plně důvěryhodných sestavení, částečně důvěryhodný. Pokud neočekáváte, že váš kód bude spuštěn z částečně důvěryhodného kontextu nebo bude volán částečně důvěryhodným kódem, nemusíte se obávat informací v této části. Pokud však píšete kód, který musí pracovat s částečně důvěryhodným kódem nebo pracovat z částečně důvěryhodného kontextu, měli byste zvážit následující faktory:  
  
- Knihovny musí být podepsány silným názvem, aby mohly být sdíleny více aplikacemi. Silné názvy umožňují, aby byl kód umístěn do globální mezipaměti sestavení nebo <xref:System.AppDomain>přidán do úplného seznamu izolovaného prostoru a umožňuje spotřebitelům ověřit, zda určitý kus mobilního kódu skutečně pochází od vás.  
  
- Ve výchozím nastavení sdílené knihovny [úrovně 1](security-transparent-code-level-1.md) se silným názvem provádějí implicitní [linkdemand](link-demands.md) pro úplnou důvěryhodnost automaticky, aniž by zapisovač knihovny musel něco dělat.  
  
- Pokud volající nemá úplný vztah důvěryhodnosti, ale stále se pokusí volat <xref:System.Security.SecurityException> takovou knihovnu, runtime vyvolá a volající není povoleno odkazovat na knihovnu.  
  
- Chcete-li zakázat automatické **LinkDemand** a zabránit vyvolání výjimky, můžete umístit **AllowPartiallyTrustedCallersAttribute** atribut na rozsah sestavení sdílené knihovny. Tento atribut umožňuje volání knihoven z částečně důvěryhodného spravovaného kódu.  
  
- Částečně důvěryhodný kód, kterému je udělen přístup ke knihovně s <xref:System.AppDomain>tímto atributem, stále podléhá dalším omezením definovaným programem .  
  
- Neexistuje žádný programový způsob, jak částečně důvěryhodný kód volat knihovnu, která nemá **Atribut AllowPartiallyTrustedCallersAttribute.**  
  
 Knihovny, které jsou soukromé pro konkrétní aplikaci, nevyžadují silný název nebo atribut **AllowPartiallyTrustedCallersAttribute** a nelze na ně odkazovat potenciálně škodlivým kódem mimo aplikaci. Takový kód je chráněn proti úmyslnému nebo neúmyslnému zneužití částečně důvěryhodným mobilním kódem, aniž by vývojář musel dělat něco navíc.  
  
 Měli byste zvážit explicitní povolení použití částečně důvěryhodným kódem pro následující typy kódu:  
  
- Kód, který byl pečlivě testován na slabá místa zabezpečení a je v souladu s pokyny popsanými v [pokynech pro bezpečné kódování](../../standard/security/secure-coding-guidelines.md).  
  
- Knihovny kódu se silným názvem, které jsou speciálně napsány pro částečně důvěryhodné scénáře.  
  
- Všechny součásti (částečně nebo plně důvěryhodné) podepsané silným názvem, který bude volán kódem staženým z Internetu.  
  
> [!NOTE]
> Některé třídy v knihovně tříd rozhraní .NET Framework nemají atribut **AllowPartiallyTrustedCallersAttribute** a nelze je volat částečně důvěryhodným kódem.  
  
## <a name="see-also"></a>Viz také

- [Zabezpečení přístupu kódu](code-access-security.md)
