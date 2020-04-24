---
title: Základy zabezpečení přístupu kódu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [.NET Framework], code access security
ms.assetid: 4eaa6535-d9fe-41a1-91d8-b437cfc16921
ms.openlocfilehash: 352fa41cb9d3136f853b068d0101a6dcab5dfd7c
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645764"
---
# <a name="code-access-security-basics"></a>Základy zabezpečení přístupu kódu

[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]

Každá aplikace, která cílí na běžný jazyk runtime (to znamená, že každá spravovaná aplikace) musí komunikovat se systémem zabezpečení runtime. Když je spravovaná aplikace načtena, její hostitel jí automaticky udělí sadu oprávnění. Tato oprávnění jsou určena místním nastavením zabezpečení hostitele nebo sandboxem, ve které se aplikace nachází. V závislosti na těchto oprávněních aplikace buď běží správně, nebo generuje výjimku zabezpečení.

Výchozí hostitel pro desktopové aplikace umožňuje spuštění kódu v plné důvěryhodnosti. Proto pokud vaše aplikace cílí na plochu, má nastavena neomezená oprávnění. Jiní hostitelé nebo karantény poskytují omezenou sadu oprávnění pro aplikace. Vzhledem k tomu, že sada oprávnění se může změnit z hostitele na hostitele, je nutné navrhnout aplikaci tak, aby používala pouze oprávnění, která umožňuje cílový hostitel.

Abyste mohli psát efektivní aplikace, které cílí na běžný jazyk runtime, musíte být seznámeni s následujícími koncepty zabezpečení přístupu kódu:

- **Typově bezpečný kód**: Kód bezpečný pro daný typ je kód, který přistupuje k typům pouze dobře definovanými a povolenými způsoby. Například daný platný odkaz na objekt, kód bezpečný pro typ může přistupovat k paměti s pevnými posuny, které odpovídají skutečným členům pole. Pokud kód přistupuje k paměti při libovolných posunech mimo rozsah paměti, která patří do veřejně exponovaných polí tohoto objektu, není typově bezpečný. Chcete-li povolit kód využívat zabezpečení přístupu kódu, musíte použít kompilátor, který generuje ověřitelně typově bezpečný kód. Další informace naleznete [v části Writing Verifiably Type-Safe Code](#typesafe_code) dále v tomto tématu.

- **Imperativní a deklarativní syntaxe**: Kód, který cílí na běžný jazyk runtime může komunikovat se systémem zabezpečení vyžádáním oprávnění, náročné, že volající mají zadaná oprávnění a přepsání určitých nastavení zabezpečení (s dostatečnými oprávněními). Dvě formy syntaxe se používají k programové interakci se systémem zabezpečení rozhraní .NET Framework: deklarativní syntaxe a imperativní syntaxe. Deklarativní volání jsou prováděna pomocí atributů; Imperativní volání se provádějí pomocí nových instancí tříd v rámci kódu. Některá volání lze provést pouze imperativně, jiné lze provádět pouze deklarativně a některá volání lze provést oběma způsoby.

- **Zabezpečené knihovny tříd**: Zabezpečená knihovna tříd používá požadavky na zabezpečení k zajištění, že volající knihovny mají oprávnění k přístupu k prostředkům, které knihovna zveřejňuje. Například zabezpečená knihovna tříd může mít metodu pro vytváření souborů, které by vyžadovaly, aby její volající měli oprávnění k vytváření souborů. Rozhraní .NET Framework se skládá ze zabezpečených knihoven tříd. Měli byste si být vědomi oprávnění potřebných pro přístup k libovolné knihovně, kterou váš kód používá. Další informace naleznete v části [Použití knihoven zabezpečených tříd](#secure_library) dále v tomto tématu.

- **Transparentní kód**: Počínaje rozhraním .NET Framework 4, kromě identifikace konkrétních oprávnění, musíte také určit, zda váš kód má být spuštěn jako transparentní pro zabezpečení. Transparentní kód zabezpečení nemůže volat typy nebo členy, které jsou označeny jako kritické pro zabezpečení. Toto pravidlo platí pro plně důvěryhodné aplikace i částečně důvěryhodné aplikace. Další informace naleznete v [tématu Security-Transparent Code](security-transparent-code.md).

<a name="typesafe_code"></a>

## <a name="writing-verifiably-type-safe-code"></a>Psaní ověřitelně typově bezpečného kódu

Kompilace just-in-time (JIT) provádí ověřovací proces, který zkoumá kód a pokusí se zjistit, zda je kód typově bezpečný. Kód, který je prokázáno, že během ověřování je typově bezpečný, se nazývá *prokazatelně typově bezpečný kód*. Kód může být typově bezpečný, ale nemusí být prokazatelně typově bezpečný z důvodu omezení ověřovacího procesu nebo kompilátoru. Ne všechny jazyky jsou bezpečné pro typ a některé kompilátory jazyka, jako je například Microsoft Visual C++, nelze generovat ověřitelně typově bezpečný spravovaný kód. Chcete-li zjistit, zda kompilátor jazyka, který používáte generuje ověřitelně typově bezpečný kód, naleznete v dokumentaci kompilátoru. Pokud používáte kompilátor jazyka, který generuje ověřitelně typově bezpečný kód pouze v případě, že se vyhnete určitým jazykovým konstrukcím, můžete použít [nástroj PEVerify](../tools/peverify-exe-peverify-tool.md) k určení, zda je váš kód prokazatelně typově bezpečný.

Kód, který není prokazatelně typově bezpečný, se může pokusit spustit, pokud zásady zabezpečení umožňují kódovitověření. Protože je však bezpečnost typů nezbytnou součástí mechanismu runtime pro izolaci sestavení, zabezpečení nelze spolehlivě vynutit, pokud kód porušuje pravidla bezpečnosti typů. Ve výchozím nastavení je povoleno spustit kód, který není typově bezpečný, pouze v případě, že pochází z místního počítače. Mobilní kód by proto měl být typově bezpečný.

<a name="secure_library"></a>

## <a name="using-secure-class-libraries"></a>Použití zabezpečených knihoven tříd

Pokud váš kód požaduje a je udělena oprávnění vyžadovaná knihovnou tříd, bude mít přístup ke knihovně a prostředky, které knihovna zveřejňuje, budou chráněny před neoprávněným přístupem. Pokud váš kód nemá příslušná oprávnění, nebude mít přístup ke knihovně tříd a škodlivý kód nebude moci použít váš kód k nepřímému přístupu k chráněným prostředkům. Jiný kód, který volá váš kód, musí mít také oprávnění k přístupu ke knihovně. Pokud tomu tak není, bude váš kód omezen spuštění také.

Zabezpečení přístupu kódu nevylučuje možnost lidské chyby v psaní kódu. Pokud však vaše aplikace používá pro přístup k chráněným prostředkům zabezpečené knihovny tříd, sníží se bezpečnostní riziko pro kód aplikace, protože knihovny tříd jsou pečlivě kontrolovány z důvodu možných problémů se zabezpečením.

## <a name="declarative-security"></a>Deklarativní zabezpečení

Deklarativní syntaxe zabezpečení používá [atributy](../../standard/attributes/index.md) k umístění informací o zabezpečení do [metadat](../../standard/metadata-and-self-describing-components.md) kódu. Atributy lze umístit na úrovni sestavení, třídy nebo člena, aby byl uveden typ požadavku, požadavku nebo přepsání, které chcete použít. Požadavky se používají v aplikacích, které cílí na soubor RUNTIME společného jazyka, aby informovaly systém zabezpečení runtime o oprávněních, která vaše aplikace potřebuje nebo nechce. Požadavky a přepsání se používají v knihovnách k ochraně prostředků před volajícími nebo k přepsání výchozího chování zabezpečení.

> [!NOTE]
> V rozhraní .NET Framework 4 došlo k důležitým změnám modelu zabezpečení a terminologie rozhraní .NET Framework. Další informace o těchto změnách naleznete v [tématu Změny zabezpečení](https://docs.microsoft.com/previous-versions/dotnet/framework/security/security-changes).

Chcete-li použít deklarativní volání zabezpečení, je nutné inicializovat data stavu objektu oprávnění tak, aby představovala konkrétní formu oprávnění, které potřebujete. Každé předdefinované oprávnění má atribut, <xref:System.Security.Permissions.SecurityAction> který je předán výčet popsat typ operace zabezpečení, které chcete provést. Oprávnění však také přijmout vlastní parametry, které jsou výhradní pro ně.

Následující fragment kódu zobrazuje deklarativní syntaxi pro požadavek, `MyPermission`aby volající vašeho kódu měli vlastní oprávnění s názvem . Toto oprávnění je hypotetické vlastní oprávnění a neexistuje v rozhraní .NET Framework. V tomto příkladu je deklarativní volání umístěno přímo před definici třídy a určuje, že toto oprávnění bude použito na úrovni třídy. Atribut je předán **SecurityAction.Demand** struktury určit, že volající musí mít toto oprávnění, aby bylo možné spustit.

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

Imperativní syntaxe zabezpečení vydává volání zabezpečení vytvořením nové instance objektu oprávnění, který chcete vyvolat. Můžete použít imperativní syntaxe k provádění požadavků a přepsání, ale ne požadavky.

Před provedením volání zabezpečení je nutné inicializovat data stavu objektu oprávnění tak, aby představovala konkrétní formu oprávnění, které potřebujete. Například při vytváření <xref:System.Security.Permissions.FileIOPermission> objektu můžete použít konstruktor k inicializaci objektu **FileIOPermission** tak, aby představoval buď neomezený přístup ke všem souborům, nebo žádný přístup k souborům. Nebo můžete použít jiný objekt **FileIOPermission,** předávání parametrů, které označují typ přístupu, který má objekt představovat (to znamená, číst, připojit nebo psát) a jaké soubory chcete objekt chránit.

Kromě použití imperativní syntaxe zabezpečení k vyvolání jednoho objektu zabezpečení jej můžete použít k inicializaci skupiny oprávnění v sadě oprávnění. Například tato technika je jediný způsob, jak spolehlivě provádět [volání assert](using-the-assert-method.md) na více oprávnění v jedné metodě. Pomocí <xref:System.Security.PermissionSet> tříd <xref:System.Security.NamedPermissionSet> y a vytvořte skupinu oprávnění a potom zavolejte příslušnou metodu k vyvolání požadovaného volání zabezpečení.

Můžete použít imperativní syntaxe k provádění požadavků a přepsání, ale ne požadavky. Můžete použít imperativní syntaxe pro požadavky a přepsání namísto deklarativní syntaxe, když informace, které potřebujete k inicializaci stavu oprávnění, jsou známy pouze za běhu. Chcete-li například zajistit, aby volající měli oprávnění ke čtení určitého souboru, ale neznáte název tohoto souboru až do běhu, použijte imperativní požadavek. Můžete také použít imperativní kontroly namísto deklarativní kontroly, když potřebujete určit za běhu, zda podmínka platí, a na základě výsledku testu, provést požadavek na zabezpečení (nebo ne).

Následující fragment kódu zobrazuje imperativní syntaxi pro požadavek, `MyPermission`aby volající vašeho kódu měli vlastní oprávnění s názvem . Toto oprávnění je hypotetické vlastní oprávnění a neexistuje v rozhraní .NET Framework. V aplikaci `MyPermission` je `MyMethod`vytvořena nová instance programu , která střeží pouze tuto metodu voláním zabezpečení.

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

Většina aplikací a součástí (s výjimkou zabezpečených knihoven) by neměla přímo volat nespravovaný kód. Existuje pro to několik důvodů. Pokud kód volá nespravovaný kód přímo, nebude povoleno spustit v mnoha případech, protože kód musí být udělena vysoká úroveň důvěryhodnosti volat nativní kód. Pokud je zásada upravena tak, aby umožňovala spuštění takové aplikace, může výrazně oslabit zabezpečení systému a ponechat aplikaci volnou pro provádění téměř jakékoli operace.

Kromě toho kód, který má oprávnění k přístupu k nespravovanému kódu může pravděpodobně provádět téměř všechny operace voláním do nespravovaného rozhraní API. Například kód, který má oprávnění k volání <xref:System.Security.Permissions.FileIOPermission> nespravovaného kódu, nemusí přistupovat k souboru. to může jen volat nespravované (Win32) soubor API přímo, obcházet spravované soubor API, které vyžaduje **FileIOPermission**. Pokud spravovaný kód má oprávnění k volání do nespravovaného kódu a volá přímo do nespravovaného kódu, systém zabezpečení nebude schopen spolehlivě vynutit omezení zabezpečení, protože runtime nemůže vynutit taková omezení na nespravovaný kód.

Pokud chcete, aby vaše aplikace provést operaci, která vyžaduje přístup k nespravovanému kódu, by to mělo učinit prostřednictvím důvěryhodné spravované třídy, která zabalí požadované funkce (pokud taková třída existuje). Nevytvářejte obálku třídy sami, pokud již existuje v knihovně zabezpečené třídy. Obálková třída, které musí být udělenvysoký stupeň důvěryhodnosti, aby bylo možné volat do nespravovaného kódu, je zodpovědná za požadavek, aby její volající měli příslušná oprávnění. Pokud používáte obálku třídy, váš kód potřebuje pouze požadovat a být udělena oprávnění, která požaduje obálky třídy.

## <a name="see-also"></a>Viz také

- <xref:System.Security.PermissionSet>
- <xref:System.Security.Permissions.FileIOPermission>
- <xref:System.Security.NamedPermissionSet>
- <xref:System.Security.Permissions.SecurityAction>
- [Assert](using-the-assert-method.md)
- [Zabezpečení přístupu kódu](code-access-security.md)
- [Základy zabezpečení přístupu kódu](code-access-security-basics.md)
- [Atributy](../../standard/attributes/index.md)
- [Metadata a součásti pro vlastní popis](../../standard/metadata-and-self-describing-components.md)
