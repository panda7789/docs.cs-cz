---
title: Transparentní kód pro zabezpečení, úroveň 2
ms.date: 03/30/2017
helpviewer_keywords:
- transparency
- level 2 transparency
- security-transparent code
- security-critical code
ms.assetid: 4d05610a-0da6-4f08-acea-d54c9d6143c0
ms.openlocfilehash: 12e991e4977b0866343158c05681ddf4bd0c869b
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645734"
---
# <a name="security-transparent-code-level-2"></a>Transparentní kód pro zabezpečení, úroveň 2

[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]

Transparentnost úrovně 2 byla zavedena v rozhraní .NET Framework 4. Tři principy tohoto modelu jsou transparentní kód, bezpečný a kritický kód zabezpečení a kód kritický pro zabezpečení.

- Transparentní kód, včetně kódu, který je spuštěn jako úplný vztah důvěryhodnosti, může volat pouze jiný transparentní kód nebo kód bezpečný a kritický pro zabezpečení. Může provádět pouze akce povolené sadou oprávnění částečné důvěryhodnosti domény (pokud existuje). Transparentní kód nemůže provést následující akce:

  - Proveďte <xref:System.Security.CodeAccessPermission.Assert%2A> zvýšení oprávnění nebo zvýšení oprávnění.

  - Obsahují nebezpečný nebo neověřitelný kód.

  - Přímo volejte kritický kód.

  - Volání nativního kódu <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> nebo kódu s atributem.

  - Volání člena, který je <xref:System.Security.Permissions.SecurityAction.LinkDemand>chráněn .

  - Dědit z kritických typů.

  Kromě toho transparentní metody nelze přepsat kritické virtuální metody nebo implementovat kritické metody rozhraní.

- Bezpečný kritický kód je plně důvěryhodný, ale je volatelný transparentním kódem. Poskytuje omezenou plochu plně důvěryhodného kódu; správnost a ověření bezpečnosti se děje v bezpečném kritickém kódu.

- Kód kritický pro zabezpečení může volat libovolný kód a je plně důvěryhodný, ale nelze jej volat transparentním kódem.

## <a name="usage-examples-and-behaviors"></a>Příklady použití a chování

Chcete-li zadat pravidla rozhraní .NET Framework 4 (průhlednost úrovně 2), použijte pro sestavení následující poznámku:

```csharp
[assembly: SecurityRules(SecurityRuleSet.Level2)]
```

Chcete-li zamknout do pravidel rozhraní .NET Framework 2.0 (průhlednost úrovně 1), použijte následující poznámku:

```csharp
[assembly: SecurityRules(SecurityRuleSet.Level1)]
```

Pokud neopatříte onotovat sestavení, pravidla rozhraní .NET Framework 4 se používají ve výchozím nastavení. Doporučeným osvědčeným postupem je <xref:System.Security.SecurityRulesAttribute> však použít atribut namísto v závislosti na výchozí.

### <a name="assembly-wide-annotation"></a>Anotace pro celou sestavu

Následující pravidla platí pro použití atributů na úrovni sestavení:

- Žádné atributy: Pokud nezadáte žádné atributy, modul runtime interpretuje veškerý kód jako kritický pro zabezpečení, s výjimkou případů, kdy kritické pro zabezpečení porušuje pravidlo dědičnosti (například při přepsání nebo implementaci transparentní virtuální metody nebo metody rozhraní). V těchto případech jsou metody bezpečné kritické. Zadání žádného atributu způsobí, že za vás určuje pravidla průhlednosti běžný jazyk.

- `SecurityTransparent`: Veškerý kód je transparentní; celé sestavení nebude dělat nic privilegovaného nebo nebezpečného.

- `SecurityCritical`: Veškerý kód, který je zaveden typy v tomto sestavení je kritická; všechny ostatní kódy jsou transparentní. Tento scénář je podobný nezadávejte žádné atributy; běžný jazyk runtime však automaticky neurčuje pravidla transparentnosti. Například pokud přepsat virtuální nebo abstraktní metody nebo implementovat metodu rozhraní, ve výchozím nastavení, tato metoda je transparentní. Je nutné explicitně anotovat `SecurityCritical` `SecuritySafeCritical`metodu jako nebo ; v opačném <xref:System.TypeLoadException> případě bude vyvolána v době načítání. Toto pravidlo platí také v případě, že základní třída a odvozené třídy jsou ve stejném sestavení.

- `AllowPartiallyTrustedCallers`(pouze úroveň 2): Všechny výchozí kódy jsou průhledné. Jednotlivé typy a členové však mohou mít jiné atributy.

Následující tabulka porovnává chování na úrovni sestavy pro úroveň 2 s úrovní 1.

|Atribut sestavení|Level 2|úroveň 1|
|------------------------|-------------|-------------|
|Žádný atribut v částečně důvěryhodném sestavení|Typy a členy jsou ve výchozím nastavení transparentní, ale mohou být kritické pro zabezpečení nebo bezpečné a kritické pro zabezpečení.|Všechny typy a členy jsou transparentní.|
|Žádný atribut|Zadání žádného atributu způsobí, že za vás určuje pravidla průhlednosti běžný jazyk. Všechny typy a členy jsou kritické pro zabezpečení, s výjimkou případů, kdy je kritické pro zabezpečení porušuje pravidlo dědičnosti.|V plně důvěryhodném sestavení (v globální mezipaměti sestavení `AppDomain`nebo identifikované jako úplný vztah důvěryhodnosti v ) jsou všechny typy transparentní a všechny členy jsou kritické pro zabezpečení.|
|`SecurityTransparent`|Všechny typy a členy jsou transparentní.|Všechny typy a členy jsou transparentní.|
|`SecurityCritical(SecurityCriticalScope.Everything)`|Neužívá se.|Všechny typy a členy jsou kritické pro zabezpečení.|
|`SecurityCritical`|Veškerý kód, který je zaveden typy v tomto sestavení je kritická; všechny ostatní kódy jsou transparentní. Pokud přepíšete virtuální nebo abstraktní metodu nebo implementujete metodu `SecurityCritical` rozhraní, musíte metodu explicitně oznamovat jako nebo `SecuritySafeCritical`.|Všechny kód výchozí transparentní. Jednotlivé typy a členové však mohou mít jiné atributy.|

### <a name="type-and-member-annotation"></a>Typ a anotace členů

Atributy zabezpečení, které jsou použity pro typ platí také pro členy, které jsou zavedeny typu. Však se nevztahují na virtuální nebo abstraktní přepsání základní třídy nebo implementace rozhraní. Pro použití atributů na úrovni typu a člena platí následující pravidla:

- `SecurityCritical`: Typ nebo člen je kritický a může být volán pouze úplným důvěryhodným kódem. Metody, které jsou zavedeny v typu kritické pro zabezpečení jsou kritické.

    > [!IMPORTANT]
    > Virtuální a abstraktní metody, které jsou zavedeny v základních třídách nebo rozhraních a přepsány nebo implementovány ve třídě kritické pro zabezpečení, jsou ve výchozím nastavení transparentní. Musí být identifikovány `SecuritySafeCritical` `SecurityCritical`jako buď nebo .

- `SecuritySafeCritical`: Typ nebo člen je bezpečný kritický. Typ nebo člen však lze volat z transparentního (částečně důvěryhodného) kódu a je stejně schopný jako jakýkoli jiný kritický kód. Kód musí být auditován z důvodu zabezpečení.

## <a name="override-patterns"></a>Přepsat vzorky

V následující tabulce jsou uvedeny přepsání metody povolené pro průhlednost úrovně 2.

|Základní člen virtuálního/rozhraní|Přepsat/rozhraní|
|------------------------------------|-------------------------|
|`Transparent`|`Transparent`|
|`Transparent`|`SafeCritical`|
|`SafeCritical`|`Transparent`|
|`SafeCritical`|`SafeCritical`|
|`Critical`|`Critical`|

## <a name="inheritance-rules"></a>Pravidla dědičnosti

V této části je přiřazena `Transparent` `Critical`následující `SafeCritical` objednávka , a kód založený na přístupu a možnostech:

`Transparent` < `SafeCritical` < `Critical`

- Pravidla pro typy: Chystáte se zleva doprava, přístup se stává více omezující. Odvozené typy musí být alespoň stejně omezující jako základní typ.

- Pravidla pro metody: Odvozené metody nemohou změnit usnadnění přístupu ze základní metody. Pro výchozí chování jsou `Transparent`všechny odvozené metody, které nejsou anotovány. Derivace kritických typů způsobit výjimku vyvolat, pokud potlačené metody `SecurityCritical`není explicitně anotován jako .

V následující tabulce jsou uvedeny vzorky dědičnosti povolených typů.

|Základní třída|Odvozenou třídu lze|
|----------------|--------------------------|
|`Transparent`|`Transparent`|
|`Transparent`|`SafeCritical`|
|`Transparent`|`Critical`|
|`SafeCritical`|`SafeCritical`|
|`SafeCritical`|`Critical`|
|`Critical`|`Critical`|

V následující tabulce jsou uvedeny nepovolené vzory dědičnosti typu.

|Základní třída|Odvozenou třídu nelze|
|----------------|-----------------------------|
|`SafeCritical`|`Transparent`|
|`Critical`|`Transparent`|
|`Critical`|`SafeCritical`|

V následující tabulce jsou uvedeny vzory dědičnosti povolené metody.

|Základní metoda|Odvozenou metodu lze|
|-----------------|---------------------------|
|`Transparent`|`Transparent`|
|`Transparent`|`SafeCritical`|
|`SafeCritical`|`Transparent`|
|`SafeCritical`|`SafeCritical`|
|`Critical`|`Critical`|

V následující tabulce jsou uvedeny vzorky dědičnosti metody, která nejsou povolena.

|Základní metoda|Odvozenou metodu nelze|
|-----------------|------------------------------|
|`Transparent`|`Critical`|
|`SafeCritical`|`Critical`|
|`Critical`|`Transparent`|
|`Critical`|`SafeCritical`|

> [!NOTE]
> Tato pravidla dědičnosti platí pro typy a členy úrovně 2. Typy v sestaveních úrovně 1 mohou dědit z typů a členů kriticképro zabezpečení úrovně 2. Proto úroveň 2 typy a členy musí mít samostatné požadavky dědičnosti pro úroveň 1 dědiců.

## <a name="additional-information-and-rules"></a>Další informace a pravidla

### <a name="linkdemand-support"></a>Podpora linkpoptávky

Model průhlednosti úrovně 2 <xref:System.Security.Permissions.SecurityAction.LinkDemand> nahradí <xref:System.Security.SecurityCriticalAttribute> atribut. Ve starším kódu (úroveň <xref:System.Security.Permissions.SecurityAction.LinkDemand> 1) je <xref:System.Security.Permissions.SecurityAction.Demand>a automaticky považována za .

### <a name="reflection"></a>Reflexe

Vyvolání kritické metody nebo čtení kritického pole spustí požadavek na úplný vztah důvěryhodnosti (stejně jako byste vyvolávali soukromou metodu nebo pole). Proto plně důvěryhodný kód může vyvolat kritickou metodu, zatímco kód s částečnou důvěryhodností nemůže.

Do <xref:System.Reflection> oboru názvů byly přidány následující vlastnosti, které určují, `SecurityCritical`zda `SecuritySafeCritical`je `SecurityTransparent` <xref:System.Type.IsSecurityCritical%2A>typ, metoda nebo pole , , nebo : , <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>, a <xref:System.Reflection.MethodBase.IsSecurityTransparent%2A>. Tyto vlastnosti slouží k určení průhlednosti pomocí odrazu namísto kontroly přítomnosti atributu. Pravidla transparentnosti jsou složitá a kontrola atributu nemusí být dostatečná.

> [!NOTE]
> Metoda `SafeCritical` vrátí `true` pro <xref:System.Type.IsSecurityCritical%2A> <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>oba `SafeCritical` a , protože je skutečně důležité (má stejné možnosti jako kritický kód, ale může být volána z transparentní kód).

Dynamické metody dědí průhlednost modulů, ke kterým jsou připojeny; nedědí průhlednost typu (pokud jsou připojeny k typu).

### <a name="skip-verification-in-full-trust"></a>Přeskočit ověření v plné důvěře

Ověření plně důvěryhodných průhledných sestavení můžete <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> přeskočit `true` nastavením vlastnosti v atributu: <xref:System.Security.SecurityRulesAttribute>

`[assembly: SecurityRules(SecurityRuleSet.Level2, SkipVerificationInFullTrust = true)]`

Vlastnost <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> je `false` ve výchozím nastavení, takže `true` vlastnost musí být nastavena na přeskočit ověření. To by mělo být provedeno pouze pro účely optimalizace. Měli byste zajistit, že transparentní kód v sestavení je `transparent` ověřitelný pomocí možnosti v [nástroji PEVerify](../tools/peverify-exe-peverify-tool.md).

## <a name="see-also"></a>Viz také

- [Transparentní kód zabezpečení, úroveň 1](security-transparent-code-level-1.md)
- [Změny zabezpečení](https://docs.microsoft.com/previous-versions/dotnet/framework/security/security-changes)
