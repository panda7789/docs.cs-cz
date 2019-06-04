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
ms.openlocfilehash: 36c3f139564b39555370cd5d41133f39c6b271bb
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2019
ms.locfileid: "66487830"
---
# <a name="security-transparent-code-level-2"></a>Transparentní kód pro zabezpečení, úroveň 2

<a name="top"></a>

[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]

Úroveň 2 transparentnost byla představena v rozhraní .NET Framework 4. Tři zásady tohoto modelu jsou transparentní kód, bezpečný a kritický pro zabezpečení kód a kód kritický pro zabezpečení.

- Transparentní kód, včetně kód, který je spuštěn při úplném vztahu důvěryhodnosti, můžete volat jiný transparentní kód nebo bezpečný a kritický pro zabezpečení pouze kód. Může pouze provádět akce povolené oprávnění částečným vztahem důvěryhodnosti domény nastavení (pokud existuje). Transparentní kód nemůže provádět následující:

  - Provést <xref:System.Security.CodeAccessPermission.Assert%2A> nebo zvýšení oprávnění.

  - Obsahovat nebezpečný nebo neověřitelný kód.

  - Přímo volejte kritický kód.

  - Volat nativní kód nebo kód s <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> atribut.

  - Volat člen, který je chráněn <xref:System.Security.Permissions.SecurityAction.LinkDemand>.

  - Dědit z kritických typů.

  Kromě toho transparentní metody nelze přepsat kritické virtuální metody nebo implementovat kritické metody rozhraní.

- Bezpečný a kritický kód je plně důvěryhodný, ale je volatelný transparentním kódem. Zpřístupňuje omezenou oblast povrchu plně důvěryhodného kódu; ověření správnosti a zabezpečení dojde v bezpečný a kritický kód.

- Kód kritický pro zabezpečení může volat libovolný kód a je plně důvěryhodný, ale nemůže být volán transparentním kódem.

Toto téma obsahuje následující oddíly:

- [Příklady použití a chování](#examples)

- [Vzory přepsání](#override)

- [Pravidla dědičnosti](#inheritance)

- [Další informace a pravidla](#additional)

<a name="examples"></a>

## <a name="usage-examples-and-behaviors"></a>Příklady použití a chování

K určování pravidel rozhraní .NET Framework 4 (transparentnosti úrovně 2), použijte následující poznámce pro sestavení:

```csharp
[assembly: SecurityRules(SecurityRuleSet.Level2)]
```

Uzavřít se do pravidel rozhraní .NET Framework 2.0 (transparentnosti úrovně 1), použijte následující poznámky:

```csharp
[assembly: SecurityRules(SecurityRuleSet.Level1)]
```

Pokud není opatřit poznámkami sestavení, se ve výchozím nastavení používají pravidla .NET Framework 4. Nicméně doporučený osvědčeným postupem je použít <xref:System.Security.SecurityRulesAttribute> atribut místo v závislosti na výchozí.

### <a name="assembly-wide-annotation"></a>Celé sestavení poznámky

Použití atributů na úrovni sestavení platí následující pravidla:

- Žádné atributy: Pokud nezadáte žádné atributy, modul runtime interpretuje celý kód jako kritické pro zabezpečení, s výjimkou případů, kde jsou kritické pro zabezpečení porušuje pravidlo dědičnosti (například když přepisuje nebo implementuje transparentní metoda rozhraní nebo virtuální). V takových případech metody jsou bezpečné a kritické. Určení žádný atribut způsobí, že modul common language runtime k určení pravidla transparentnosti za vás.

- `SecurityTransparent`: Všechny kódy jsou transparentní; celé sestavení nespustí žádnou akci privilegovaných nebo unsafe.

- `SecurityCritical`: Veškerý kód, který je zavedený typy v tomto sestavení je velmi důležité; všechny ostatní kód je transparentní. Tento scénář je podobný bez zadání jakékoli atributů Nicméně modul common language runtime automaticky nezjišťuje pravidla transparentnosti. Například pokud přepsat virtuální nebo abstraktní metody nebo implementaci metody rozhraní, ve výchozím nastavení tato metoda je transparentní. Musíte explicitně označit metody jako `SecurityCritical` nebo `SecuritySafeCritical`; v opačném případě <xref:System.TypeLoadException> bude vyvolána v okamžiku načtení. Toto pravidlo platí také, pokud základní třída a odvozené třídy jsou ve stejném sestavení.

- `AllowPartiallyTrustedCallers` (pouze pro úroveň 2): Všechny výchozí hodnoty pro transparentní kód. Nicméně jednotlivé typy a členy mohou mít jiné atributy.

Následující tabulka porovnává chování úrovně sestavení pro úrovně 2 s 1. úrovně.

|Atribut sestavení|Úroveň 2|úroveň 1|
|------------------------|-------------|-------------|
|Žádný atribut pro částečně důvěryhodná sestavení|Typy a členy jsou ve výchozím nastavení transparentní, ale může být kritické pro zabezpečení nebo bezpečný a kritický pro zabezpečení.|Všechny typy a členy jsou transparentní.|
|Žádný atribut|Určení žádný atribut způsobí, že modul common language runtime k určení pravidla transparentnosti za vás. Všechny typy a členy jsou kritické pro zabezpečení, s výjimkou případů, kde jsou kritické pro zabezpečení porušuje pravidlo dědičnosti.|Pro plně důvěryhodná sestavení (v globální mezipaměti sestavení nebo označen jako úplný vztah důvěryhodnosti v `AppDomain`) jsou všechny typy transparentní a všichni členové jsou bezpečné a kritické pro zabezpečení.|
|`SecurityTransparent`|Všechny typy a členy jsou transparentní.|Všechny typy a členy jsou transparentní.|
|`SecurityCritical(SecurityCriticalScope.Everything)`|Není k dispozici.|Všechny typy a členy jsou kritické pro zabezpečení.|
|`SecurityCritical`|Veškerý kód, který je zavedený typy v tomto sestavení je velmi důležité; všechny ostatní kód je transparentní. Je-li přepsat virtuální nebo abstraktní metody nebo implementovat metodu rozhraní, musíte explicitně označit metody jako `SecurityCritical` nebo `SecuritySafeCritical`.|Všechny výchozí hodnoty pro transparentní kód. Nicméně jednotlivé typy a členy mohou mít jiné atributy.|

### <a name="type-and-member-annotation"></a>Typ a člen poznámek

Atributy zabezpečení, které se použijí na typ. platí také pro členy, které vznikají zavlečením typu. Nicméně se nevztahují na virtuální nebo abstraktní přepíše z implementací základní třídy nebo rozhraní. Použití atributů na úrovni typů a členů platí následující pravidla:

- `SecurityCritical`: Tento typ nebo člen je velmi důležité a může být volána pouze pomocí plně důvěryhodného kódu. Metody, které jsou součástí typu kritické pro zabezpečení jsou kritické.

    > [!IMPORTANT]
    > Virtuální a abstraktní metody, které jsou součástí základní třídy nebo rozhraní a přepsat nebo implementována ve třídě kritické z hlediska zabezpečení je ve výchozím nastavení transparentní. Musí být určen buď `SecuritySafeCritical` nebo `SecurityCritical`.

- `SecuritySafeCritical`: Tento typ nebo člen je kritický. Tento typ nebo člen lze volat z transparentního kódu (částečně důvěryhodným) a je možností, jako jakýkoli jiný kritický kód. Musí být auditován kód pro zabezpečení.

[Zpět na začátek](#top)

<a name="override"></a>

## <a name="override-patterns"></a>Vzory přepsání

V následující tabulce jsou uvedeny přepsání metody, které jsou povolené pro transparentnosti úrovně 2.

|Základní virtuálního člena/člena rozhraní|Přepsání a interface|
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

- Pravidla pro typy: Přechod zleva doprava, bude přístup více omezující. Odvozené typy musí být alespoň tak omezující jako základního typu.

- Pravidla pro metody: Odvozené metody nemůže změnit přístupnost ze základní metody. Pro výchozí chování, jsou všechny odvozené metody, která nejsou označena `Transparent`. Odvozené typy kritických typů způsobit výjimku, která je vyvolána, pokud přepsané metody není explicitně označena jako `SecurityCritical`.

V následující tabulce jsou uvedeny povolený typ vzory dědičnosti.

|Základní třída|Odvozená třída může být|
|----------------|--------------------------|
|`Transparent`|`Transparent`|
|`Transparent`|`SafeCritical`|
|`Transparent`|`Critical`|
|`SafeCritical`|`SafeCritical`|
|`SafeCritical`|`Critical`|
|`Critical`|`Critical`|

Následující tabulka ukazuje zakázaného typ vzory dědičnosti.

|Základní třída|Odvozená třída nemůže být|
|----------------|-----------------------------|
|`SafeCritical`|`Transparent`|
|`Critical`|`Transparent`|
|`Critical`|`SafeCritical`|

V následující tabulce jsou uvedeny povolené metody vzory dědičnosti.

|Base – metoda|Může být Odvozená metoda|
|-----------------|---------------------------|
|`Transparent`|`Transparent`|
|`Transparent`|`SafeCritical`|
|`SafeCritical`|`Transparent`|
|`SafeCritical`|`SafeCritical`|
|`Critical`|`Critical`|

Následující tabulka ukazuje zakázaného metodu vzory dědičnosti.

|Base – metoda|Nemůže být Odvozená metoda|
|-----------------|------------------------------|
|`Transparent`|`Critical`|
|`SafeCritical`|`Critical`|
|`Critical`|`Transparent`|
|`Critical`|`SafeCritical`|

> [!NOTE]
> Tato pravidla dědičnosti se vztahují na typy a členy úrovně 2. Typy v sestaveních úroveň 1 může dědit z typy kritické pro zabezpečení úrovně 2 a členy. Typy a členy úrovně 2 proto musí mít samostatné dědičnost požadavků pro dědice úrovně 1.

[Zpět na začátek](#top)

<a name="additional"></a>

## <a name="additional-information-and-rules"></a>Další informace a pravidla

### <a name="linkdemand-support"></a>Podpora LinkDemand

Nahradí modelu transparentnosti úrovně 2 <xref:System.Security.Permissions.SecurityAction.LinkDemand> s <xref:System.Security.SecurityCriticalAttribute> atribut. V kódu starší verze (úroveň 1) <xref:System.Security.Permissions.SecurityAction.LinkDemand> je automaticky považováno za <xref:System.Security.Permissions.SecurityAction.Demand>.

### <a name="reflection"></a>Reflexe

Vyvolání kritické metody nebo čtení kritickému poli spustí požadavek pro úplný vztah důvěryhodnosti (tak, jako kdyby byly vyvolání soukromou metodu nebo pole). Proto plně důvěryhodného kódu můžete vyvolat na kritickou metodu, že nelze částečně důvěryhodného kódu.

Následující vlastnosti byly přidány do <xref:System.Reflection> obor názvů pro určení, zda je typ, metodu nebo pole `SecurityCritical`, `SecuritySafeCritical`, nebo `SecurityTransparent`: <xref:System.Type.IsSecurityCritical%2A>, <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>, a <xref:System.Reflection.MethodBase.IsSecurityTransparent%2A>. Tyto vlastnosti lze použijte k určení transparentnosti pomocí reflexe namísto kontroly na přítomnost atributu. Pravidla transparentnosti jsou komplexní a kontrola pro atribut nemusí být dostatečné.

> [!NOTE]
> A `SafeCritical` vrátí metoda `true` pro obě <xref:System.Type.IsSecurityCritical%2A> a <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>, protože `SafeCritical` je skutečně důležité (má stejné funkce jako kritický kód, ale mohou být volány transparentní kód).

Průhlednost modulů, které jsou připojeny k; dědit dynamických metod nedědí průhlednost typu (pokud jsou připojeny k typu).

### <a name="skip-verification-in-full-trust"></a>Přeskočit ověřování v režimu plné důvěryhodnosti

Můžete přeskočit ověření pro plně důvěryhodná transparentní sestavení tak, že nastavíte <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> vlastnost `true` v <xref:System.Security.SecurityRulesAttribute> atribut:

`[assembly: SecurityRules(SecurityRuleSet.Level2, SkipVerificationInFullTrust = true)]`

<xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> Vlastnost `false` ve výchozím nastavení, tak vlastnost musí být nastavena na `true` pro přeskočení ověření. To by mělo být provedeno za účelem optimalizace pouze. Měli byste zajistit, že transparentní kód v sestavení je ověřit pomocí `transparent` možnost [Nástroj PEVerify](../../../docs/framework/tools/peverify-exe-peverify-tool.md).

## <a name="see-also"></a>Viz také:

- [Kód transparentní pro zabezpečení, úroveň 1](../../../docs/framework/misc/security-transparent-code-level-1.md)
- [Změny zabezpečení](../../../docs/framework/security/security-changes.md)
