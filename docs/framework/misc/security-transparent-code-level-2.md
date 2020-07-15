---
title: Transparentní kód pro zabezpečení, úroveň 2
description: Pochopení transparentního kódu úrovně 2 Podívejte se na příklady a chování použití, přepište vzory, pravidla dědičnosti a další.
ms.date: 03/30/2017
helpviewer_keywords:
- transparency
- level 2 transparency
- security-transparent code
- security-critical code
ms.assetid: 4d05610a-0da6-4f08-acea-d54c9d6143c0
ms.openlocfilehash: 3b87a48ac3f9925fd868be9e58d5904014ca6c09
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/14/2020
ms.locfileid: "86309206"
---
# <a name="security-transparent-code-level-2"></a>Transparentní kód pro zabezpečení, úroveň 2

[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]

Transparentnost úrovně 2 byla představena v .NET Framework 4. Tři principy tohoto modelu jsou transparentní kód, bezpečný a kritický kód pro zabezpečení a kód kritický pro zabezpečení.

- Transparentní kód, včetně kódu, který je spuštěn jako úplný vztah důvěryhodnosti, může volat jiný transparentní kód nebo pouze bezpečný kód kritický pro zabezpečení. Může provádět jenom akce, které povoluje sada oprávnění částečné důvěryhodnosti domény (pokud existuje). Transparentní kód nemůže provádět následující:

  - Provedení <xref:System.Security.CodeAccessPermission.Assert%2A> nebo zvýšení oprávnění.

  - Obsahuje nezabezpečený nebo neověřitelný kód.

  - Přímo zavolejte kritický kód.

  - Volejte nativní kód nebo kód s <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> atributem.

  - Zavolejte člen, který je chráněn pomocí <xref:System.Security.Permissions.SecurityAction.LinkDemand> .

  - Dědí z kritických typů.

  Transparentní metody navíc nemohou přepsat kritické virtuální metody nebo implementovat kritické metody rozhraní.

- Bezpečný a kritický kód je plně důvěryhodný, ale je volat transparentním kódem. Zveřejňuje omezený plošný prostor s plně důvěryhodným kódem; k ověření správnosti a zabezpečení dochází v kódu bezpečného kritického.

- Kód kritický pro zabezpečení může volat jakýkoli kód a je plně důvěryhodný, ale nemůže být volán transparentním kódem.

## <a name="usage-examples-and-behaviors"></a>Příklady využití a chování

Chcete-li zadat pravidla .NET Framework 4 (transparentnost úrovně 2), použijte následující anotaci pro sestavení:

```csharp
[assembly: SecurityRules(SecurityRuleSet.Level2)]
```

Chcete-li zamknout pravidla .NET Framework 2,0 (transparentnost první úrovně), použijte následující poznámku:

```csharp
[assembly: SecurityRules(SecurityRuleSet.Level1)]
```

Pokud do sestavení nechcete přidat poznámku, použijí se ve výchozím nastavení pravidla .NET Framework 4. Doporučený osvědčený postup je však použít <xref:System.Security.SecurityRulesAttribute> atribut místo v závislosti na výchozím nastavení.

### <a name="assembly-wide-annotation"></a>Poznámka na úrovni sestavení

Následující pravidla platí pro použití atributů na úrovni sestavení:

- Bez atributů: modul runtime interpretuje veškerý kód jako kritické pro zabezpečení, s výjimkou případů, kdy je kritické zabezpečení v rozporu s pravidlem dědičnosti (například při přepsání nebo implementaci transparentní virtuální nebo metody rozhraní). V těchto případech jsou metody kritické. Zadání žádného atributu způsobí, že modul CLR (Common Language Runtime) určí pravidla transparentnosti.

- `SecurityTransparent`: Veškerý kód je transparentní; celé sestavení neprovede žádné privilegované nebo nezabezpečené.

- `SecurityCritical`: Všechny kódy, které jsou představeny typy v tomto sestavení, jsou kritické; všechny ostatní kódy jsou transparentní. Tento scénář je podobný jako při zadávání jakýchkoli atributů; modul CLR (Common Language Runtime) ale neurčuje automaticky pravidla transparentnosti. Například pokud přepíšete virtuální nebo abstraktní metodu nebo implementujete metodu rozhraní, je tato metoda ve výchozím nastavení průhledná. Metodu musíte explicitně opatřit poznámkami jako `SecurityCritical` nebo `SecuritySafeCritical` . v opačném případě <xref:System.TypeLoadException> dojde k vyvolání v době načítání. Toto pravidlo platí také v případě, že je základní třída i odvozená třída ve stejném sestavení.

- `AllowPartiallyTrustedCallers`(pouze úroveň 2): výchozí hodnota je transparentní pro všechny kódy. Jednotlivé typy a členy však mohou mít jiné atributy.

Následující tabulka porovnává chování na úrovni sestavení pro úroveň 2 s úrovní 1.

|Atribut Assembly|Level 2|úroveň 1|
|------------------------|-------------|-------------|
|Žádný atribut v částečně důvěryhodném sestavení|Typy a členy jsou ve výchozím nastavení transparentní, ale mohou být kritické pro zabezpečení nebo bezpečné – kritické.|Všechny typy a členy jsou transparentní.|
|Žádný atribut|Zadání žádného atributu způsobí, že modul CLR (Common Language Runtime) určí pravidla transparentnosti. Všechny typy a členy jsou kritické pro zabezpečení, s výjimkou případů, kdy kritické zabezpečení porušují pravidlo dědičnosti.|V plně důvěryhodném sestavení (v globální mezipaměti sestavení (GAC) nebo identifikovaný jako úplný vztah důvěryhodnosti v rámci `AppDomain` ) jsou všechny typy transparentní a všechny členy jsou bezpečné – kritické.|
|`SecurityTransparent`|Všechny typy a členy jsou transparentní.|Všechny typy a členy jsou transparentní.|
|`SecurityCritical(SecurityCriticalScope.Everything)`|Neužívá se.|Všechny typy a členy jsou kritické pro zabezpečení.|
|`SecurityCritical`|Všechny kódy, které jsou představeny typy v tomto sestavení jsou kritické; všechny ostatní kódy jsou transparentní. Pokud přepíšete virtuální nebo abstraktní metodu nebo implementujete metodu rozhraní, je nutné explicitně opatřit poznámkami metodu jako `SecurityCritical` nebo `SecuritySafeCritical` .|Veškerý kód je standardně transparentní. Jednotlivé typy a členy však mohou mít jiné atributy.|

### <a name="type-and-member-annotation"></a>Typ a Poznámka člena

Atributy zabezpečení použité pro typ platí také pro členy, které jsou zavedeny typem. Neplatí však pro virtuální nebo abstraktní přepsání implementace základní třídy nebo rozhraní. Následující pravidla platí pro použití atributů na úrovni typu a člena:

- `SecurityCritical`: Typ nebo člen je kritický a může být volán pouze pomocí plně důvěryhodného kódu. Metody, které jsou představeny v typu kritickém pro zabezpečení, jsou kritické.

    > [!IMPORTANT]
    > Virtuální a abstraktní metody, které jsou představeny v základních třídách nebo rozhraních a jsou přepsány nebo implementovány ve třídě kritické pro zabezpečení, jsou standardně transparentní. Musí být identifikovány buď `SecuritySafeCritical` nebo `SecurityCritical` .

- `SecuritySafeCritical`: Typ nebo člen je v kritickém stavu. Typ nebo člen je však možné volat z transparentního (částečně důvěryhodného) kódu a je stejně schopný jako jakýkoliv jiný kritický kód. Kód musí být auditován z důvodu zabezpečení.

## <a name="override-patterns"></a>Vzory přepsání

Následující tabulka ukazuje přepsání metody povolené pro transparentnost úrovně 2.

|Základní člen virtuálního/rozhraní|Přepsat/rozhraní|
|------------------------------------|-------------------------|
|`Transparent`|`Transparent`|
|`Transparent`|`SafeCritical`|
|`SafeCritical`|`Transparent`|
|`SafeCritical`|`SafeCritical`|
|`Critical`|`Critical`|

## <a name="inheritance-rules"></a>Pravidla dědičnosti

V této části je následující pořadí přiřazeno k `Transparent` kódu, `Critical` a na `SafeCritical` základě přístupu a možností:

`Transparent` < `SafeCritical` < `Critical`

- Pravidla pro typy: Přejít zleva doprava a přístup se bude více omezující. Odvozené typy musí být alespoň tak omezující jako základní typ.

- Pravidla pro metody: odvozené metody nemohou změnit přístupnost ze základní metody. Pro výchozí chování jsou všechny odvozené metody, které nejsou opatřeny poznámkami `Transparent` . Deriváty kritických typů způsobují výjimku, pokud přepsaná metoda není explicitně označena jako `SecurityCritical` .

Následující tabulka uvádí povolené vzory dědičnosti typů.

|Základní třída|Odvozená třída může být|
|----------------|--------------------------|
|`Transparent`|`Transparent`|
|`Transparent`|`SafeCritical`|
|`Transparent`|`Critical`|
|`SafeCritical`|`SafeCritical`|
|`SafeCritical`|`Critical`|
|`Critical`|`Critical`|

V následující tabulce jsou uvedeny nepovolené vzory dědičnosti typů.

|Základní třída|Odvozená třída nemůže být|
|----------------|-----------------------------|
|`SafeCritical`|`Transparent`|
|`Critical`|`Transparent`|
|`Critical`|`SafeCritical`|

Následující tabulka uvádí povolené vzory dědičnosti metod.

|Základní metoda|Odvozená metoda může být|
|-----------------|---------------------------|
|`Transparent`|`Transparent`|
|`Transparent`|`SafeCritical`|
|`SafeCritical`|`Transparent`|
|`SafeCritical`|`SafeCritical`|
|`Critical`|`Critical`|

V následující tabulce jsou uvedeny nepovolené vzory dědičnosti metod.

|Základní metoda|Odvozená metoda nemůže být|
|-----------------|------------------------------|
|`Transparent`|`Critical`|
|`SafeCritical`|`Critical`|
|`Critical`|`Transparent`|
|`Critical`|`SafeCritical`|

> [!NOTE]
> Tato pravidla dědičnosti platí pro typy a členy úrovně 2. Typy v sestaveních úrovně 1 mohou dědit z typů a členů kritických pro zabezpečení úrovně 2. Typy a členy úrovně 2 proto musí mít samostatné požadavky dědičnosti pro dědice úrovně 1.

## <a name="additional-information-and-rules"></a>Další informace a pravidla

### <a name="linkdemand-support"></a>Podpora LinkDemand

Model transparentnosti úrovně 2 nahrazuje <xref:System.Security.Permissions.SecurityAction.LinkDemand> <xref:System.Security.SecurityCriticalAttribute> Atribut atributem. Ve starší verzi (úroveň 1) <xref:System.Security.Permissions.SecurityAction.LinkDemand> je automaticky považován za <xref:System.Security.Permissions.SecurityAction.Demand> .

### <a name="reflection"></a>Reflexe

Vyvolání kritické metody nebo čtení kritického pole aktivuje požadavek na úplný vztah důvěryhodnosti (stejně jako v případě, že jste vyvolali soukromou metodu nebo pole). Proto kód s úplným vztahem důvěryhodnosti může vyvolat kritickou metodu, zatímco kód částečného vztahu důvěryhodnosti nemůže.

Následující vlastnosti byly přidány do <xref:System.Reflection> oboru názvů, aby bylo možné určit, zda typ, metoda nebo pole jsou `SecurityCritical` , `SecuritySafeCritical` nebo `SecurityTransparent` : <xref:System.Type.IsSecurityCritical%2A> , <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A> , a <xref:System.Reflection.MethodBase.IsSecurityTransparent%2A> . Pomocí těchto vlastností lze určit průhlednost pomocí reflexe namísto kontroly přítomnosti atributu. Pravidla transparentnosti jsou složitá a kontrola atributu nemusí být dostačující.

> [!NOTE]
> `SafeCritical`Metoda vrátí `true` pro obojí <xref:System.Type.IsSecurityCritical%2A> a <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A> , protože `SafeCritical` je skutečně kritická (má stejné možnosti jako kritický kód, ale může být volána z transparentního kódu).

Dynamické metody dědí průhlednost modulů, ke kterým jsou připojené; nedědí průhlednost typu (pokud jsou připojeny k typu).

### <a name="skip-verification-in-full-trust"></a>Přeskočit ověřování v úplném vztahu důvěryhodnosti

Můžete přeskočit ověření pro plně důvěryhodná transparentní sestavení nastavením <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> vlastnosti na hodnotu `true` v <xref:System.Security.SecurityRulesAttribute> atributu:

`[assembly: SecurityRules(SecurityRuleSet.Level2, SkipVerificationInFullTrust = true)]`

<xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A>Vlastnost je `false` ve výchozím nastavení, takže vlastnost musí být nastavena na hodnotu `true` pro přeskočení ověření. Tato operace by se měla provádět jenom pro účely optimalizace. Je nutné zajistit, aby transparentní kód v sestavení byl ověřen pomocí `transparent` Možnosti v [nástroji Nástroj PEVerify](../tools/peverify-exe-peverify-tool.md).

## <a name="see-also"></a>Viz také

- [Kód transparentní pro zabezpečení, úroveň 1](security-transparent-code-level-1.md)
- [Změny zabezpečení](https://docs.microsoft.com/previous-versions/dotnet/framework/security/security-changes)
