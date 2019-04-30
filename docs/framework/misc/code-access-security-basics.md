---
title: Základy zabezpečení přístupu kódu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [.NET Framework], code access security
ms.assetid: 4eaa6535-d9fe-41a1-91d8-b437cfc16921
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8d5a5658fcb6bbba72938a16a9e5c82fd779e2e3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61868768"
---
# <a name="code-access-security-basics"></a>Základy zabezpečení přístupu kódu

[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]

Každou aplikaci, která se zaměřuje na modul common language runtime (to znamená, že všechny spravované aplikace) musí spolupracovat s systém zabezpečení modulu runtime. Spravované aplikace je načtena, jeho hostitel je automaticky přidělí sadu oprávnění. Tato oprávnění jsou určeny podle hostitele místní nastavení zabezpečení nebo aplikace se nachází v izolovaném prostoru. V závislosti na oprávněních aplikace bude fungovat správně nebo vygeneruje výjimku zabezpečení.

Výchozí hostitel pro desktopové aplikace umožňuje spuštění v režimu plné důvěryhodnosti kódu. Proto pokud vaše aplikace cílí na ploše, má neomezený oprávnění nastavena. Další hostitele nebo izolované prostory poskytují omezené oprávnění nastavena pro aplikace. Vzhledem k tomu, že sada oprávnění můžete změnit mezi hostiteli, je třeba navrhnout vaše aplikace pro použití pouze oprávnění, která umožňuje cílového hostitele.

Znáte tyto koncepty zabezpečení přístupu kódu musí být k zapsání efektivní aplikací využívajících common language runtime:

- **Kód zajišťující bezpečnost typů**: Typově bezpečný kód je kód, který přistupuje k typům pouze dobře definovanými, přípustnými způsoby. Například s ohledem odkaz na platný objekt, kód zajišťující bezpečnost typů můžete přístup k paměti na pevné posuny, které odpovídají skutečné pole členů. Pokud kód přistupuje k paměťově na libovolné pozici mimo oblast paměti, která patří do tohoto objektu veřejně vystavené pole, není typově bezpečný. Chcete-li kód, abyste využili výhod zabezpečení přístupu kódu, je nutné použít kompilátor, který generuje kód ověřitelně bezpečného typu. Další informace najdete v tématu [zápis prokazatelně typově bezpečný kód](#typesafe_code) později v tomto tématu.

- **Imperativní a deklarativní syntaxe**: Kód, který napadá modul common language runtime můžete pracovat s tím systém zabezpečení o oprávnění, náročné, že volající zadali oprávnění a přepsání některých nastavení zabezpečení (zadaný dostatečná oprávnění). Používat dvě formy syntaxe programově pracovat systém zabezpečení rozhraní .NET Framework: deklarativní nebo imperativní syntaxi. Deklarativní volání se provádí pomocí atributů imperativní volání se provádí pomocí nové instance třídy v rámci vašeho kódu. Některá volání lze provést pouze imperativně, jiné mohou být provedeny pouze deklarativně a provést několik volání buď způsobem.

- **Zabezpečené knihovny tříd**: Knihovny zabezpečení tříd používá k zajištění, že volající knihovny mají oprávnění pro přístup k prostředkům, které knihovna poskytuje požadavky na zabezpečení. Knihovny zabezpečení tříd může například mít metodu pro vytváření souborů, které by vyžadují, aby jeho volající nemá oprávnění k vytvoření souborů. Rozhraní .NET Framework se skládá z knihoven zabezpečených tříd. Je třeba vědět oprávnění požadovaná pro přístup k libovolné knihovny, který váš kód používá. Další informace najdete v tématu [pomocí knihovny zabezpečení tříd](#secure_library) později v tomto tématu.

- **Transparentní kód**: Počínaje [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], kromě identifikace konkrétní oprávnění, musíte také určit, jestli váš kód by měl spustit jako transparentní pro zabezpečení. Kód transparentní pro zabezpečení nelze volat typy nebo členy, které jsou identifikovány jako kritické pro zabezpečení. Toto pravidlo platí pro plně důvěryhodné aplikace, jakož i částečně důvěryhodné aplikace. Další informace najdete v tématu [kód transparentní pro zabezpečení](../../../docs/framework/misc/security-transparent-code.md).

<a name="typesafe_code"></a>

## <a name="writing-verifiably-type-safe-code"></a>Psát kód Ověřitelně bezpečného typu

Kompilace just-in-time (JIT) provádí procesem ověření, který zkontroluje kód a pokusí se zjistit, jestli je kód typově bezpečný. Je volána kód, který je ověřené během ověření jako typově bezpečný *prokazatelně typově bezpečný kód*. Kód může být typově bezpečný, ještě nemusí být ověřitelně bezpečného typu z důvodu omezení procesu ověřování nebo kompilátoru. Ne všechny jazyky jsou typově bezpečné a některé kompilátory jazyka, jako je například Microsoft Visual C++, nelze generovat spravovaný kód ověřitelně bezpečného typu. Pokud chcete zjistit, zda kompilátor jazyka, který používáte generuje kód ověřitelně bezpečného typu, v dokumentaci kompilátoru. Pokud používáte kompilátor jazyka, které generují kód ověřitelně bezpečného typu pouze v případě, že se vyhnete určitým jazykovým konstrukcím, můžete chtít použít [Nástroj PEVerify](../../../docs/framework/tools/peverify-exe-peverify-tool.md) zjistit, jestli je váš kód ověřitelně bezpečného typu.

Kód, který není ověřitelně bezpečného typu můžete zkusit spustit, pokud zásady zabezpečení umožňuje obejít ověření kódu. Ale protože bezpečnost typů je základní součástí modulu runtime mechanismus pro izolující sestavení, zabezpečení nelze spolehlivě vynutit, pokud kód porušuje pravidla bezpečnost typů. Ve výchozím nastavení kód, který není typově bezpečný může spustit pouze v případě, že pochází z místního počítače. Proto mobilní kód by měl být typově bezpečné.

<a name="secure_library"></a>

## <a name="using-secure-class-libraries"></a>Používání knihoven zabezpečených tříd

Pokud váš kód vyžádá a je uděleno oprávnění požadovaná knihovna tříd, bude možné přístup do knihovny a prostředky, které knihovna poskytuje budou chráněná před neoprávněným přístupem. Pokud váš kód nemá příslušná oprávnění, se nebudou moct dostat ke knihovně třídy a škodlivý kód nebude možné použít kód nepřímo přístup k chráněným prostředkům. Jiný kód, který volá váš kód musí mít také oprávnění pro přístup ke knihovně. Pokud tomu tak není, budou mít omezené váš kód spuštěn rovněž.

Zabezpečení přístupu kódu není eliminuje možnost lidské chyby při psaní kódu. Nicméně pokud vaše aplikace používá knihoven zabezpečených tříd pro přístup k chráněným prostředkům, bezpečnostní riziko pro kód aplikace dojde k omezení, protože knihovny tříd jsou kontrolovány úzce pro potenciální problémy se zabezpečením.

## <a name="declarative-security"></a>Deklarativní zabezpečení

Deklarativní syntaxe zabezpečení používá [atributy](../../../docs/standard/attributes/index.md) umístit informace o zabezpečení do [metadat](../../../docs/standard/metadata-and-self-describing-components.md) kódu. Atributy mohou být umístěny na úrovni sestavení, třída nebo člen k označení typu požadavek, poptávku nebo přepsání, které chcete použít. Požadavky se používají v aplikacích, které se zaměřují na modul common language runtime k informování o oprávnění, která vaše aplikace potřebuje nebo nechce systému zabezpečení modulu runtime. Požadavky a přepsání se používají v knihovnách pomoct chránit prostředky z volající nebo přepsat výchozí chování zabezpečení.

> [!NOTE]
> V [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], byly důležité změny v modelu zabezpečení rozhraní .NET Framework a terminologii. Další informace o těchto změnách najdete v tématu [změny zabezpečení](../../../docs/framework/security/security-changes.md).

Chcete-li použít volání deklarativní zabezpečení, musíte inicializovat data o stavu objektu oprávnění tak, aby představuje určitou formu oprávnění, které potřebujete. Každé z předdefinovaných oprávnění má atribut, který je předán <xref:System.Security.Permissions.SecurityAction> výčet popisující typ operace zabezpečení, kterou chcete provést. Oprávnění však přijmout jejich vlastní parametry, které jsou výhradně pro jejich.

Následující fragment kódu ukazuje deklarativní syntaxe pro vyžádání, že volající vašeho kódu mají vlastní oprávnění s názvem `MyPermission`. Toto oprávnění je hypotetický vlastní oprávnění a neexistuje v rozhraní .NET Framework. V tomto příkladu je uskutečněn deklarativní hovor přímo před definici třídy určující, že toto oprávnění se použije na úrovni třídy. Atribut je předán **SecurityAction.Demand** struktury k určení, že volající musí mít toto oprávnění, aby bylo možné spustit.

```vb
<MyPermission(SecurityAction.Demand, Unrestricted = True)> Public Class MyClass1

   Public Sub New()
      'The constructor is protected by the security call.
   End Sub

   Public Sub MyMethod()
      'This method is protected by the security call.
   End Sub

   Public Sub YourMethod()
      'This method is protected by the security call.
   End Sub
End Class
```

```csharp
[MyPermission(SecurityAction.Demand, Unrestricted = true)]
public class MyClass
{
   public MyClass()
   {
      //The constructor is protected by the security call.
   }

   public void MyMethod()
   {
      //This method is protected by the security call.
   }

   public void YourMethod()
   {
      //This method is protected by the security call.
   }
}
```

## <a name="imperative-security"></a>Imperativní zabezpečení

Imperativní syntaxe zabezpečení řeší tím, že vytvoříte novou instanci oprávnění objektu, který chcete vyvolat volání zabezpečení. Imperativní syntaxe slouží k provádění požadavků a přepsání, ale ne požadavků.

Než provedete volání zabezpečení, musíte inicializovat data o stavu objektu oprávnění tak, aby představuje určitou formu oprávnění, které potřebujete. Například při vytváření <xref:System.Security.Permissions.FileIOPermission> objektu, můžete použít konstruktor k inicializaci **FileIOPermission** objektu tak, aby představuje buď neomezený přístup ke všem souborům nebo žádný přístup k souborům. Nebo můžete použít jinou **FileIOPermission** objektu, parametrů, které označují typ přístupu, které chcete předat objekt představují (to znamená, čtení, připojte nebo zápisu) a které soubory chcete objekt, který chcete chránit.

Kromě použití imperativní syntaxe zabezpečení, který má být vyvolán jediného objektu zabezpečení, ho můžete použít k inicializaci skupiny oprávnění v sadě oprávnění. Například tato technika je jediný způsob, jak spolehlivě provést [vyhodnocení](../../../docs/framework/misc/using-the-assert-method.md) vyžaduje více oprávnění v jedné metody. Použití <xref:System.Security.PermissionSet> a <xref:System.Security.NamedPermissionSet> třídy pro vytvoření skupiny oprávnění a poté zavolejte metodu vhodné k vyvolání volání požadované pro zabezpečení.

Imperativní syntaxe slouží k provádění požadavků a přepsání, ale ne požadavků. Imperativní syntaxe může použít pro požadavky a přepíše místo deklarativní syntaxe při informace potřebné k inicializaci stav oprávnění stanou známými pouze v době běhu. Například pokud chcete zajistit, že volající nemá oprávnění ke čtení určitých souborů, ale název tohoto souboru až do běhu si nejste jisti, použijte imperativní požadavky. Také můžete používat imperativní kontroly místo deklarativní kontroly, když je potřeba určit v době běhu, zda obsahuje podmínku a na základě výsledku testu, vytvořit požadavek zabezpečení (nebo nemusíte).

Následující fragment kódu ukazuje imperativní syntaxe pro vyžádání, že volající vašeho kódu mají vlastní oprávnění s názvem `MyPermission`. Toto oprávnění je hypotetický vlastní oprávnění a neexistuje v rozhraní .NET Framework. Novou instanci třídy `MyPermission` se vytvoří v `MyMethod`, důslednější pouze této metody pomocí volání zabezpečení.

```vb
Public Class MyClass1

   Public Sub New()

   End Sub

   Public Sub MyMethod()
      'MyPermission is demanded using imperative syntax.
      Dim Perm As New MyPermission()
      Perm.Demand()
      'This method is protected by the security call.
   End Sub

   Public Sub YourMethod()
      'YourMethod 'This method is not protected by the security call.
   End Sub
End Class
```

```csharp
public class MyClass {
   public MyClass(){

   }

   public void MyMethod() {
       //MyPermission is demanded using imperative syntax.
       MyPermission Perm = new MyPermission();
       Perm.Demand();
       //This method is protected by the security call.
   }

   public void YourMethod() {
       //This method is not protected by the security call.
   }
}
```

## <a name="using-managed-wrapper-classes"></a>Použití tříd spravovaných obálek

Většina aplikací a komponent (s výjimkou zabezpečené knihovny) by neměl přímo volat nespravovaný kód. Existuje několik důvodů. Pokud kód volá nespravovaný kód přímo, se nebudou moct spustit v mnoha případech platí, protože musíte kódu udělit vysoký stupeň důvěryhodnosti volat nativní kód. Pokud zásady je upravit tak, aby povolit spuštění takové aplikace, se výrazně oslabit zabezpečení systému, pokud aplikace můžete provádět téměř všechny operace.

Kromě toho kód, který má oprávnění pro přístup k nespravovanému kódu pravděpodobně může provádět téměř všechny operace voláním nespravovaného rozhraní API. Například kód, který má oprávnění pro volání nespravovaného kódu není nutné <xref:System.Security.Permissions.FileIOPermission> pro přístup k souboru; může volat jenom nespravované rozhraní API přímo, bez použití souboru spravované rozhraní API, které vyžaduje souboru (Win32) **FileIOPermission**. Pokud spravovaný kód má oprávnění k volání nespravovaného kódu a volají přímo do nespravovaného kódu, bude systém zabezpečení nelze spolehlivě vynucovat bezpečnostní omezení, protože modul runtime nemůže vynutit taková omezení na nespravovaný kód.

Pokud chcete aplikaci k provedení operace, která vyžaduje přístup k nespravovanému kódu, je to měl dělat implementovaný pomocí důvěryhodného spravovanou třídu, která obaluje požadovanou funkci (je-li takové třídy existuje). Nevytvářejte obálkovou třídu sami Pokud už existuje v zabezpečené knihovny tříd. Obálková třída, která musí být poskytnuta vysoký stupeň důvěryhodnosti bude moct volat nespravovaný kód, je zodpovědný za náročné, že jeho volající nemá příslušná oprávnění. Pokud používáte obálkovou třídu, váš kód pouze musí k vyžádání a udělit oprávnění, která vyžaduje obálkovou třídu.

## <a name="see-also"></a>Viz také:

- <xref:System.Security.PermissionSet>
- <xref:System.Security.Permissions.FileIOPermission>
- <xref:System.Security.NamedPermissionSet>
- <xref:System.Security.Permissions.SecurityAction>
- [Kontrolní výraz](../../../docs/framework/misc/using-the-assert-method.md)
- [Zabezpečení přístupu kódu](../../../docs/framework/misc/code-access-security.md)
- [Základy zabezpečení přístupu kódu](../../../docs/framework/misc/code-access-security-basics.md)
- [Atributy](../../../docs/standard/attributes/index.md)
- [Metadata a komponenty popisující samy sebe](../../../docs/standard/metadata-and-self-describing-components.md)
