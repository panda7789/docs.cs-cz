---
title: Transparentní kód pro zabezpečení, úroveň 2
ms.date: 03/30/2017
helpviewer_keywords:
- transparency
- level 2 transparency
- security-transparent code
- security-critical code
ms.assetid: 4d05610a-0da6-4f08-acea-d54c9d6143c0
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0f15c3bc097bc034db41c95cd168104b8435aaf0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="security-transparent-code-level-2"></a>Transparentní kód pro zabezpečení, úroveň 2
<a name="top"></a>
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 Průhlednost úrovně 2 byla zavedena v [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]. Tři zásady tohoto modelu jsou transparentní kód, bezpečné a kritické pro zabezpečení kód a kód kritický pro zabezpečení.  
  
-   Transparentní kód, včetně kódu, který je spuštěný jako úplný vztah důvěryhodnosti, můžete volat jiný transparentní kód nebo pouze bezpečné a kritické pro zabezpečení kód. Může provádět jenom akce povolené oprávnění částečné důvěryhodnosti domény nastavené (pokud existuje). Kód transparentní nelze provést následující akce:  
  
    -   Provést <xref:System.Security.CodeAccessPermission.Assert%2A> nebo zvýšení úrovně oprávnění.  
  
    -   Obsahovat nebezpečný nebo neověřitelný kód.  
  
    -   Kód kritický pro volejte přímo.  
  
    -   Volání nativního kódu nebo kód s <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> atribut.  
  
    -   Volání člena, který je chráněn <xref:System.Security.Permissions.SecurityAction.LinkDemand>.  
  
    -   Typy kritické dědí.  
  
     Kromě toho transparentní metody nelze přepsat kritické virtuální metody nebo implementovat kritické metody rozhraní.  
  
-   Kritická kód je plně důvěryhodný, ale je volatelné transparentní kód. Zpřístupňuje omezenou oblast povrchu plné důvěryhodnosti kódu; dojde k ověření správnosti a zabezpečení v kritickém kódu.  
  
-   Kód kritický pro zabezpečení můžete volat žádný kód a je plně důvěryhodný, ale ji nelze volat kód transparentní.  
  
 Toto téma obsahuje následující oddíly:  
  
-   [Příklady použití a chování](#examples)  
  
-   [Vzory přepsání](#override)  
  
-   [Pravidla dědičnosti](#inheritance)  
  
-   [Další informace a pravidla](#additional)  
  
<a name="examples"></a>   
## <a name="usage-examples-and-behaviors"></a>Příklady použití a chování  
 Chcete-li určit [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] pravidla (průhlednost úrovně 2), použijte následující anotaci pro sestavení:  
  
```  
[assembly: SecurityRules(SecurityRuleSet.Level2)]  
```  
  
 Pokud chcete uzamknout na rozhraní .NET Framework 2.0 pravidla (úroveň 1 průhlednost), použijte následující poznámky:  
  
```  
[assembly: SecurityRules(SecurityRuleSet.Level1)]  
```  
  
 Pokud není opatřit poznámkami sestavení, [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] pravidla se používají ve výchozím nastavení. Doporučený osvědčený postup je však používat <xref:System.Security.SecurityRulesAttribute> atribut místo v závislosti na výchozí.  
  
### <a name="assembly-wide-annotation"></a>Sestavení celou poznámky  
 Následující pravidla platí při použití atributů na úrovni sestavení:  
  
-   Žádné atributy: Pokud nezadáte žádné atributy, modul runtime interpretuje všechny kód jako kritické pro zabezpečení, s výjimkou případů, kdy se kritický pro zabezpečení porušuje pravidlo dědičnosti (například v případě, že přepsání nebo implementace transparentní virtuální nebo rozhraní – metoda ). V takových případech jsou kritická metody. Určení žádný atribut způsobí, že modul common language runtime k určení pravidel průhlednost.  
  
-   `SecurityTransparent`: Všechna kód je transparentní; celé sestavení nebude dělat nic privilegovaného nebo unsafe.  
  
-   `SecurityCritical`: Všechna kód, který je zavedený typy v tomto sestavení je velmi důležité; všechny ostatní kód je transparentní. Tento scénář je podobná nespecifikuje žádné atributy; však modul common language runtime automaticky neurčuje pravidla průhlednost. Například pokud přepíšete metodu virtuální nebo abstraktní nebo implementovat metodu rozhraní, ve výchozím nastavení, že metoda je transparentní. Musíte explicitně označit jako metodu `SecurityCritical` nebo `SecuritySafeCritical`, jinak hodnota <xref:System.TypeLoadException> při načítání, bude vyvolána. Toto pravidlo platí i v případě základní třída a odvozené třídy jsou ve stejném sestavení.  
  
-   `AllowPartiallyTrustedCallers` (úroveň 2 pouze): všechny code automaticky transparentní. Jednotlivé typy a členy však mohou mít jiné atributy.  
  
 Následující tabulka porovnává chování úrovně sestavení úroveň 2 s úrovně 1.  
  
|Atribut sestavení|Úroveň 2|úroveň 1|  
|------------------------|-------------|-------------|  
|Žádný atribut v částečně důvěryhodné sestavení|Typy a členové jsou ve výchozím nastavení transparentní, ale může být kritické pro zabezpečení nebo bezpečné a kritické pro zabezpečení.|Všechny typy a členy jsou transparentní.|  
|Žádný atribut|Určení žádný atribut způsobí, že modul common language runtime k určení pravidel průhlednost. Všechny typy a členy jsou kritické pro zabezpečení, s výjimkou případů, kdy se kritický pro zabezpečení porušuje pravidlo dědičnosti.|Ve plně důvěryhodný pro sestavení (v globální mezipaměti sestavení nebo identifikován jako úplný vztah důvěryhodnosti v `AppDomain`) jsou všechny typy transparentní a bezpečné a kritické pro zabezpečení se všichni její členové.|  
|`SecurityTransparent`|Všechny typy a členy jsou transparentní.|Všechny typy a členy jsou transparentní.|  
|`SecurityCritical(SecurityCriticalScope.Everything)`|Nelze použít.|Všechny typy a členy jsou kritické pro zabezpečení.|  
|`SecurityCritical`|Všechny kód, který je zavedený typy v tomto sestavení je velmi důležité; všechny ostatní kód je transparentní. Pokud přepíšete metodu virtuální nebo abstraktní nebo implementovat metodu rozhraní, musíte explicitně označit jako metodu `SecurityCritical` nebo `SecuritySafeCritical`.|Všechny kódu automaticky transparentní. Jednotlivé typy a členy však mohou mít jiné atributy.|  
  
### <a name="type-and-member-annotation"></a>Typ a člen poznámky  
 Atributy zabezpečení, které se použijí na typ platí také pro členy, které jsou zavedené podle typu. Ale nelze je použít na virtuální nebo přepsání abstraktní základní implementace třídy nebo rozhraní. Následující pravidla platí při použití atributů na úrovni typu a členu:  
  
-   `SecurityCritical`: Typ nebo člen je velmi důležité a lze volat pouze ve plně důvěryhodný kód. Metody, které jsou zavedené v kritické pro zabezpečení typu jsou důležité.  
  
    > [!IMPORTANT]
    >  Virtuální a abstraktní metody, které jsou zavedené v rozhraní nebo základní třídy a přepsat nebo implementována ve třídě kritické pro zabezpečení jsou transparentní ve výchozím nastavení. Musí být identifikovány jako `SecuritySafeCritical` nebo `SecurityCritical`.  
  
-   `SecuritySafeCritical`: Typ nebo člen je kritický. Typ nebo člen lze volat z kódu transparentní (částečně důvěryhodné) a je umožňující jako jakýkoli jiný kód, kritické. Kód musí být auditován pro zabezpečení.  
  
 [Zpět na začátek](#top)  
  
<a name="override"></a>   
## <a name="override-patterns"></a>Vzory přepsání  
 V následující tabulce jsou uvedeny přepsání metody povolené pro průhlednost úrovně 2.  
  
|Základní virtuální/rozhraní člen|Přepsání/rozhraní|  
|------------------------------------|-------------------------|  
|`Transparent`|`Transparent`|  
|`Transparent`|`SafeCritical`|  
|`SafeCritical`|`Transparent`|  
|`SafeCritical`|`SafeCritical`|  
|`Critical`|`Critical`|  
  
 [Zpět na začátek](#top)  
  
<a name="inheritance"></a>   
## <a name="inheritance-rules"></a>Pravidla dědičnosti  
 V této části je přiřazená následující pořadí `Transparent`, `Critical`, a `SafeCritical` kódu na základě přístupu a možnosti:  
  
 `Transparent` < `SafeCritical` < `Critical`  
  
-   Pravidla pro typy: přejdete zleva doprava, bude přístup k více omezující. Odvozené typy musí být nejméně omezující jako základního typu.  
  
-   Pravidla pro metody: odvozené metody nelze změnit usnadnění ze základní metody. Výchozí chování, jsou všechny odvozené metody, které nejsou poznámkou `Transparent`. Odvozené typy kritické způsobují výjimku, která je vyvolána, pokud přepsaná metoda není explicitně označena jako `SecurityCritical`.  
  
 Následující tabulka zobrazuje typ povolené vzory dědičnosti.  
  
|Base – třída|Odvozená třída může být|  
|----------------|--------------------------|  
|`Transparent`|`Transparent`|  
|`Transparent`|`SafeCritical`|  
|`Transparent`|`Critical`|  
|`SafeCritical`|`SafeCritical`|  
|`SafeCritical`|`Critical`|  
|`Critical`|`Critical`|  
  
 Následující tabulka zobrazuje typ nepovoleném vzory dědičnosti.  
  
|Base – třída|Nemůže být odvozené třídy|  
|----------------|-----------------------------|  
|`SafeCritical`|`Transparent`|  
|`Critical`|`Transparent`|  
|`Critical`|`SafeCritical`|  
  
 Následující tabulka zobrazuje povolené metoda vzory dědičnosti.  
  
|Base – metoda|Může být odvozené – metoda|  
|-----------------|---------------------------|  
|`Transparent`|`Transparent`|  
|`Transparent`|`SafeCritical`|  
|`SafeCritical`|`Transparent`|  
|`SafeCritical`|`SafeCritical`|  
|`Critical`|`Critical`|  
  
 Následující tabulka zobrazuje metodu nepovoleném vzory dědičnosti.  
  
|Base – metoda|Nemůže být odvozené – metoda|  
|-----------------|------------------------------|  
|`Transparent`|`Critical`|  
|`SafeCritical`|`Critical`|  
|`Critical`|`Transparent`|  
|`Critical`|`SafeCritical`|  
  
> [!NOTE]
>  Tato pravidla dědičnosti se vztahují na úroveň 2 typy a členy. Typy v sestavení úroveň 1 může dědit vlastnosti z typy kritické pro zabezpečení na úrovni 2 a členy. Typy na úrovni 2 a členy proto musí mít samostatné dědičnost požadavků pro dědice úroveň 1.  
  
 [Zpět na začátek](#top)  
  
<a name="additional"></a>   
## <a name="additional-information-and-rules"></a>Další informace a pravidla  
  
### <a name="linkdemand-support"></a>Podpora LinkDemand  
 Nahradí model průhlednost úrovně 2 <xref:System.Security.Permissions.SecurityAction.LinkDemand> s <xref:System.Security.SecurityCriticalAttribute> atribut. V kódu starší verze (úroveň 1) <xref:System.Security.Permissions.SecurityAction.LinkDemand> automaticky považován za <xref:System.Security.Permissions.SecurityAction.Demand>.  
  
### <a name="reflection"></a>Reflexe  
 Vyvolání kritické metody nebo čtení kritické položky spustí požadavek na úplný vztah důvěryhodnosti (stejně, jako kdyby byly vyvolání soukromá metoda nebo pole). Kód plné důvěryhodnosti tedy můžete vyvolat kritickou metodu, zatímco nelze částečně důvěryhodný kód.  
  
 Následující vlastnosti jsou přidané do <xref:System.Reflection> oboru názvů určete, zda je typ, metoda nebo pole `SecurityCritical`, `SecuritySafeCritical`, nebo `SecurityTransparent`: <xref:System.Type.IsSecurityCritical%2A>, <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>, a <xref:System.Reflection.MethodBase.IsSecurityTransparent%2A>. Použijte tyto vlastnosti k určení transparentnosti pomocí reflexe místo kontroly na přítomnost atribut. Pravidla transparentnosti jsou komplexní a kontrola atributu nemusí být plně dostačující.  
  
> [!NOTE]
>  A `SafeCritical` metoda vrátí `true` pro obě <xref:System.Type.IsSecurityCritical%2A> a <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>, protože `SafeCritical` je skutečně kritická (má stejné schopnosti jako kód kritický pro, ale může být volána z transparentní kód).  
  
 Dynamické metody dědí transparentnost modulů, které jsou připojené k; nedědí transparentnost typu (pokud jsou připojené k typu).  
  
### <a name="skip-verification-in-full-trust"></a>Přeskočit ověření v režimu plné důvěryhodnosti  
 Můžete přeskočit ověření pro plně důvěryhodná transparentní sestavení pomocí nastavení <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> vlastnost `true` v <xref:System.Security.SecurityRulesAttribute> atribut:  
  
 `[assembly: SecurityRules(SecurityRuleSet.Level2, SkipVerificationInFullTrust = true)]`  
  
 <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> Vlastnost je `false` ve výchozím nastavení, takže vlastnost musí být nastavená `true` pro přeskočení ověření. To by mělo být provedeno pouze pro účely optimalizace. Měli byste zajistit, že transparentní kód v sestavení je ověřitelný pomocí `transparent` možnost [Nástroj PEVerify](../../../docs/framework/tools/peverify-exe-peverify-tool.md).  
  
## <a name="see-also"></a>Viz také  
 [Kód transparentní pro zabezpečení, úroveň 1](../../../docs/framework/misc/security-transparent-code-level-1.md)  
 [Změny zabezpečení](../../../docs/framework/security/security-changes.md)
