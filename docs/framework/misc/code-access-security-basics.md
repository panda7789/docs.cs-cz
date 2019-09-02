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
ms.openlocfilehash: d77683dde24eeec5de7f1e541a6cc86f3b0c6617
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205635"
---
# <a name="code-access-security-basics"></a>Základy zabezpečení přístupu kódu

[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]

Každá aplikace, která cílí na modul CLR (Common Language Runtime) (to znamená, že každá spravovaná aplikace) musí komunikovat se systémem zabezpečení modulu runtime. Po načtení spravované aplikace mu hostitel automaticky udělí sadu oprávnění. Tato oprávnění jsou určena místním nastavením zabezpečení hostitele nebo izolovaným prostorem (sandbox), ve kterém se aplikace nachází. V závislosti na těchto oprávněních se aplikace buď správně spustí, nebo vygeneruje výjimku zabezpečení.

Výchozí hostitel pro desktopové aplikace umožňuje spuštění kódu v úplném vztahu důvěryhodnosti. Proto pokud vaše aplikace cílí na plochu, má neomezenou sadu oprávnění. Jiní hostitelé nebo izolované prostory poskytují sadu omezených oprávnění pro aplikace. Vzhledem k tomu, že sada oprávnění se může změnit z hostitele na hostitele, je nutné navrhnout aplikaci tak, aby používala pouze oprávnění, která povoluje váš cílový hostitel.

Aby bylo možné zapisovat efektivní aplikace zaměřené na modul CLR (Common Language Runtime), musíte být obeznámeni s následujícími koncepty zabezpečení přístupu kódu.

- **Kód zajišťující bezpečnost typů**: Typově bezpečný kód je kód, který přistupuje pouze k typům v dobře definovaných, přípustných způsobech. Například s ohledem na platný odkaz na objekt může kód bezpečný pro zápis získat přístup k paměti s pevnými posuny, které odpovídají skutečným členům pole. Pokud kód přistupuje k paměti s libovolnými posuny mimo rozsah paměti, která patří do veřejně vydaných polí daného objektu, není typově bezpečná. Chcete-li povolit kód pro zvýhodnění zabezpečení přístupu kódu, je nutné použít kompilátor, který generuje ověřitelný kód zajišťující bezpečnost typů. Další informace naleznete v části [psaní typově bezpečného kódu](#typesafe_code) dále v tomto tématu.

- **Imperativní a deklarativní syntaxe**: Kód, který cílí na modul CLR (Common Language Runtime), může komunikovat se systémem zabezpečení tím, že požaduje oprávnění, vyžaduje, aby volající určil oprávnění a přepsala určitá nastavení zabezpečení (s dostatečnými oprávněními). Pomocí dvou forem syntaxe můžete programově komunikovat s .NET Framework systém zabezpečení: deklarativní syntaxe a imperativní syntaxe. Deklarativní volání jsou prováděna pomocí atributů; imperativní volání jsou prováděna pomocí nových instancí třídy v rámci kódu. Některá volání lze provést pouze imperativně, jiné mohou být provedeny pouze deklarativně a některá volání lze provádět buď způsobem.

- **Zabezpečené knihovny tříd**: Zabezpečená knihovna tříd používá požadavky na zabezpečení, aby zajistila, že volající knihovny mají oprávnění pro přístup k prostředkům, které knihovna zpřístupňuje. Například knihovna zabezpečených tříd může mít metodu pro vytváření souborů, které by vyžadovaly, že volající mají oprávnění k vytváření souborů. .NET Framework se skládá z bezpečnostních knihoven tříd. Měli byste si uvědomit o oprávněních potřebných pro přístup k libovolné knihovně, kterou používá váš kód. Další informace najdete v části [použití zabezpečených knihoven tříd](#secure_library) dále v tomto tématu.

- **Transparentní kód**: Počínaje .NET Framework 4, kromě určení konkrétních oprávnění, musíte také určit, jestli by měl být váš kód spuštěný jako transparentní z hlediska zabezpečení. Kód transparentní z hlediska zabezpečení nemůže volat typy nebo členy, které jsou identifikovány jako kritické pro zabezpečení. Toto pravidlo se vztahuje na aplikace s plnou důvěryhodností i částečně důvěryhodné aplikace. Další informace najdete v tématu [Kód transparentní pro zabezpečení](security-transparent-code.md).

<a name="typesafe_code"></a>

## <a name="writing-verifiably-type-safe-code"></a>Zápis ověřitelného kódu bezpečného typu

Kompilace just-in-time (JIT) provádí proces ověření, který prověřuje kód a pokusí se zjistit, zda je kód typově bezpečný. Kód, který je ověřen při ověřování, je typově bezpečný, se nazývá *ověřitelný kód zajišťující bezpečnost typů*. Kód může být typově bezpečný, ale nemusí být ověřitelný typově bezpečný, protože má omezení procesu ověřování nebo kompilátoru. Ne všechny jazyky jsou typově bezpečné a některé kompilátory jazyka, jako je Microsoft Visual C++, nemůžou generovat ověřitelný kód zabezpečený typově bezpečným způsobem. Chcete-li zjistit, zda kompilátor jazyka, který používáte, vygeneruje ověřitelný typově bezpečný kód, prostudujte si dokumentaci k kompilátoru. Použijete-li kompilátor jazyka, který generuje ověřitelný kód ověřovatele pouze v případě, že se vyhnete určitým jazykovým konstrukcím, můžete použít [Nástroj Nástroj PEVerify](../tools/peverify-exe-peverify-tool.md) k určení, zda je kód ověřovatelně typově bezpečný.

Kód, který není ověřitelný typově bezpečný, se může pokusit provést, pokud zásady zabezpečení umožní kódu obejít ověření. Nicméně, protože bezpečnost typů je podstatnou součástí mechanismu modulu runtime pro izolaci sestavení, zabezpečení nelze spolehlivě vyhovět, pokud kód narušuje pravidla bezpečnosti typů. Ve výchozím nastavení může být kód, který není typově bezpečný, spuštěn pouze v případě, že pochází z místního počítače. Mobilní kód by proto měl být typově bezpečný.

<a name="secure_library"></a>

## <a name="using-secure-class-libraries"></a>Použití zabezpečených knihoven tříd

Pokud váš kód požaduje a má udělená oprávnění požadovaná knihovnou tříd, bude mít povolen přístup ke knihovně a prostředky, které zpřístupňuje knihovna, budou chráněny před neoprávněným přístupem. Pokud váš kód nemá příslušná oprávnění, nebude mít přístup k knihovně tříd a škodlivý kód nebude moci používat váš kód pro nepřímo přístup k chráněným prostředkům. Další kód, který volá váš kód, musí mít také oprávnění pro přístup ke knihovně. Pokud tomu tak není, váš kód bude také omezen.

Zabezpečení přístupu kódu neeliminuje možnost lidské chyby při psaní kódu. Nicméně pokud vaše aplikace používá pro přístup k chráněným prostředkům zabezpečené knihovny tříd, bezpečnostní riziko pro kód aplikace je sníženo, protože knihovny tříd jsou pečlivě kontrolovány na potenciální problémy se zabezpečením.

## <a name="declarative-security"></a>Deklarativní zabezpečení

Deklarativní syntaxe zabezpečení používá [atributy](../../standard/attributes/index.md) k umístění informací o zabezpečení do [metadat](../../standard/metadata-and-self-describing-components.md) vašeho kódu. Atributy lze umístit na úrovni sestavení, třídy nebo člena, chcete-li určit typ požadavku, poptávku nebo přepsání, který chcete použít. Žádosti se používají v aplikacích, které cílí na modul CLR (Common Language Runtime), aby informovaly systém zabezpečení modulu runtime o oprávněních, která vaše aplikace potřebuje nebo nechce. Požadavky a přepsání se používají v knihovnách k ochraně prostředků před volajícími nebo pro přepsání výchozího chování zabezpečení.

> [!NOTE]
> V .NET Framework 4 existovaly důležité změny modelu a terminologie zabezpečení .NET Framework. Další informace o těchto změnách najdete v tématu [změny zabezpečení](../security/security-changes.md).

Aby bylo možné použít deklarativní volání zabezpečení, je nutné inicializovat stavová data objektu oprávnění tak, aby představovalo konkrétní tvar oprávnění, která potřebujete. Každé integrované oprávnění má atribut, který je předaný <xref:System.Security.Permissions.SecurityAction> výčtu k popisu typu operace zabezpečení, kterou chcete provést. Nicméně oprávnění také přijímají vlastní parametry, které jsou pro ně výhradně.

Následující fragment kódu ukazuje deklarativní syntaxi pro vyžádání, že volající vašeho kódu mají vlastní oprávnění volána `MyPermission`. Toto oprávnění je hypotetické vlastní oprávnění a neexistuje v .NET Framework. V tomto příkladu je deklarativní volání umístěno přímo před definicí třídy, což určuje, že toto oprávnění je použito na úrovni třídy. Atributu je předána struktura **SecurityAction. Demand** , která určuje, že volající musí mít toto oprávnění, aby je bylo možné spustit.

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

Imperativní syntaxe zabezpečení vydá bezpečnostní volání vytvořením nové instance objektu oprávnění, který chcete vyvolat. K provedení požadavků a přepsání, ale ne požadavků, lze použít imperativní syntaxi.

Před provedením tohoto volání zabezpečení je nutné inicializovat stavová data objektu oprávnění tak, aby představovalo konkrétní tvar oprávnění, která potřebujete. Například při vytváření <xref:System.Security.Permissions.FileIOPermission> objektu můžete použít konstruktor k inicializaci objektu **FileIOPermission** tak, aby představoval buď neomezený přístup ke všem souborům, nebo žádný přístup k souborům. Nebo můžete použít jiný objekt **FileIOPermission** , předání parametrů, které určují typ přístupu, který má objekt představovat (tj. čtení, připojení nebo zápis) a jaké soubory chcete objektu chránit.

Kromě použití imperativní syntaxe zabezpečení k vyvolání jediného objektu zabezpečení jej můžete použít k inicializaci skupiny oprávnění v sadě oprávnění. Například tato technika je jediným způsobem, jak spolehlivě provést volání [Assert](using-the-assert-method.md) u více oprávnění v jedné metodě. Pomocí tříd <xref:System.Security.NamedPermissionSet> a vytvořte skupinu oprávnění a pak zavolejte odpovídající metodu pro vyvolání požadovaného bezpečnostního volání. <xref:System.Security.PermissionSet>

K provedení požadavků a přepsání, ale ne požadavků, lze použít imperativní syntaxi. Můžete použít imperativní syntaxi pro požadavky a přepsání namísto deklarativní syntaxe, pokud informace, které potřebujete k inicializaci stavu oprávnění, se nazývají pouze v době běhu. Například pokud chcete zajistit, že volající mají oprávnění ke čtení určitého souboru, ale neznáte název tohoto souboru, dokud nespustíte čas spuštění, použijte imperativní požadavek. Můžete také použít imperativní kontroly namísto deklarativních kontrol, pokud potřebujete určit dobu běhu, ať už podmínka obsahuje, a na základě výsledku testu udělat požadavek na zabezpečení (nebo ne).

Následující fragment kódu ukazuje imperativní syntaxi pro vyžádání, že volající vašeho kódu mají vlastní oprávnění volána `MyPermission`. Toto oprávnění je hypotetické vlastní oprávnění a neexistuje v .NET Framework. `MyPermission` V`MyMethod`systému je vytvořena nová instance, která chrání pouze tuto metodu s voláním zabezpečení.

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

Většina aplikací a součástí (s výjimkou zabezpečených knihoven) by neměla přímo volat nespravovaný kód. Z tohoto důvodu je k dispozici několik důvodů. Pokud kód volá přímo nespravovaný kód, nebudete moci spustit v mnoha případech, protože kód musí mít vysokou úroveň důvěryhodnosti pro volání nativního kódu. Pokud je zásada upravena tak, aby umožňovala spuštění takové aplikace, může významně oslabit zabezpečení systému, což zanechává aplikaci volnou pro provedení téměř jakékoli operace.

Kromě toho kód, který má oprávnění pro přístup k nespravovanému kódu, může pravděpodobně provést téměř jakoukoli operaci voláním do nespravovaného rozhraní API. Například kód, který má oprávnění k volání nespravovaného kódu <xref:System.Security.Permissions.FileIOPermission> , nevyžaduje přístup k souboru; může jednoduše volat nespravované rozhraní API souboru (Win32) přímo a obejít spravované rozhraní API spravovaného souboru, které vyžaduje **FileIOPermission**. Pokud má spravovaný kód oprávnění pro volání do nespravovaného kódu a volá přímo do nespravovaného kódu, systém zabezpečení nebude schopen spolehlivě vymáhat omezení zabezpečení, protože modul runtime nemůže vymáhat taková omezení nespravovaného kódu.

Pokud chcete, aby aplikace prováděla operaci, která vyžaduje přístup k nespravovanému kódu, měl by tak učinit prostřednictvím důvěryhodné spravované třídy, která zabalí požadovanou funkci (pokud taková třída existuje). Nevytvářejte obálkovou třídu sami, pokud již existuje v zabezpečené knihovně tříd. Obálková třída, která musí být udělena vysokým stupněm důvěryhodnosti, aby bylo možné uskutečnit volání do nespravovaného kódu, zodpovídá za to, že volající mají příslušná oprávnění. Použijete-li obálkovou třídu, váš kód musí pouze požádat o oprávnění, která Obálková třída požaduje.

## <a name="see-also"></a>Viz také:

- <xref:System.Security.PermissionSet>
- <xref:System.Security.Permissions.FileIOPermission>
- <xref:System.Security.NamedPermissionSet>
- <xref:System.Security.Permissions.SecurityAction>
- [Uplatňuje](using-the-assert-method.md)
- [Zabezpečení přístupu kódu](code-access-security.md)
- [Základy zabezpečení přístupu ke kódu](code-access-security-basics.md)
- [Atributy](../../standard/attributes/index.md)
- [Metadata a komponenty popisující samy sebe](../../standard/metadata-and-self-describing-components.md)
