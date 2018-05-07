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
ms.openlocfilehash: 77687934a91b92909bdbab1ede5075ace4326d4e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="code-access-security-basics"></a>Základy zabezpečení přístupu kódu
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 Každá aplikace, která cílí modul common language runtime (to znamená, každá spravované aplikace) musí spolupracovat s modulem runtime zabezpečení systému. Pokud spravované aplikace je načtena, jeho hostitel je automaticky přidělí sadu oprávnění. Tato oprávnění jsou určena pomocí nastavení zabezpečení hostitele nebo pomocí izolovaného prostoru, které je aplikace. V závislosti na tato oprávnění aplikace buď běží správně, nebo vygeneruje výjimka zabezpečení.  
  
 Výchozího hostitele pro aplikací klasické pracovní plochy umožňuje kód pro spuštění v režimu plné důvěryhodnosti. Proto pokud aplikace cílí na plochu, má neomezený oprávnění nastavená. Jiným hostitelům nebo izolovaných prostorů poskytují omezené oprávnění nastavená pro aplikace. Protože sadu oprávnění, můžete změnit mezi hostiteli, je třeba navrhnout vaše aplikace používat jenom oprávnění, která umožňuje cílového hostitele.  
  
 Musíte být obeznámeni s následující koncepty zabezpečení přístupu kódu k psaní aplikací efektivní cílených modul common language runtime:  
  
-   **Typově bezpečný kód**: bezpečnost typů kód je kód, který přistupuje k typům pouze způsoby dobře definovaný, povolená. Třeba platný objekt odkazu na daný, bezpečnost typů kódu můžete získat přístup k paměti na pevné pozici, které odpovídají skutečným pole členů. Pokud kód přistupuje k paměťově na libovolné pozici mimo rozsah paměti, která patří do tohoto objektu veřejně zveřejněné pole, není bezpečnost typů. Chcete-li kód, abyste mohli využívat výhod zabezpečení přístupu kódu, je nutné použít kompilátoru, která generuje typ ověřitelný kód. Další informace najdete v tématu [psaní zajišťující bezpečnost bezpečnost typů kódu](#typesafe_code) později v tomto tématu.  
  
-   **Imperativní a deklarativní syntaxe**: kód, který je cílem modul common language runtime mohou komunikovat se systémem zabezpečení pomocí vyžadování oprávnění náročné, zda volající zadali oprávnění a přepsání určité (nastavení zabezpečení zadané dostatečná oprávnění). Používat dvě formy syntaxe prostřednictvím kódu programu interakci se systémem zabezpečení rozhraní .NET Framework: deklarativní nebo imperativní syntaxi. Deklarativní volání jsou prováděna pomocí atributů imperativní volání jsou prováděna pomocí nové instance tříd v rámci vašeho kódu. Některá volání lze provést pouze imperativní, jiné mohou být provedeny pouze deklarativně a některá volání lze provést buď způsobem.  
  
-   **Zabezpečené knihovny tříd**: zabezpečené knihovny tříd používá k zajištění, že volající knihovny mají oprávnění pro přístup k prostředkům, které knihovna poskytuje požadavky na zabezpečení. Zabezpečené knihovny tříd může mít například metodu pro vytvoření souborů, které by požadovat, aby její volající měli oprávnění k vytvoření souborů. Rozhraní .NET Framework se skládá z zabezpečené knihovny tříd. Byste měli znát oprávnění požadovaná pro přístup k žádné knihovny, která používá váš kód. Další informace najdete v tématu [pomocí knihovny tříd zabezpečení](#secure_library) později v tomto tématu.  
  
-   **Kód transparentní pro**: od verze [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], kromě identifikace konkrétních oprávnění musí také zjistíte, zda váš kód se má spustit jako transparentní pro zabezpečení. Kód transparentní pro zabezpečení nelze volat typy nebo členy, kteří jsou identifikovány jako kritické pro zabezpečení. Toto pravidlo se vztahuje na plně důvěryhodné aplikace a také částečně důvěryhodné aplikace. Další informace najdete v tématu [kód transparentní pro zabezpečení](../../../docs/framework/misc/security-transparent-code.md).  
  
<a name="typesafe_code"></a>   
## <a name="writing-verifiably-type-safe-code"></a>Zápis typ ověřitelný kód  
 Kompilace za běhu (JIT) provede ověření procesu, který kontroluje kód a pokusí se zjistit, zda kód je bezpečnost typů. Kód, který je ověřené během ověření zajistit bezpečnost typů se nazývá *typ ověřitelný kód s*. Kód může být bezpečnost typů, ještě nemusí být typ ověřitelný z důvodu omezení proces ověření nebo kompilátoru. Ne všechny jazyky jsou jazyky bezpečnost typů a některé kompilátory jazyka, jako je například Microsoft Visual C++, nelze vygenerovat typ ověřitelný spravovaného kódu. Pokud chcete zjistit, jestli kompilátor jazyka, který používáte generuje typ ověřitelný kód, projděte si dokumentaci k kompilátoru. Pokud používáte kompilátor jazyka, který generuje typ ověřitelný kód jenom v případě, že se vyhnout určité jazykové konstrukty, můžete chtít použít [Nástroj PEVerify](../../../docs/framework/tools/peverify-exe-peverify-tool.md) k určení, zda kód je typ ověřitelný.  
  
 Kód, který není typu ověřitelný pokuste se spustit, pokud zásady zabezpečení umožňuje obejít ověření kódu. Ale protože typ zabezpečení je nedílnou součást vámi vyžádaných mechanismus modulu runtime pro uzavírací sestavení, zabezpečení nelze spolehlivě vynutit, pokud kód porušuje pravidla zabezpečení typů. Ve výchozím nastavení je kód, který není bezpečný povoleno spustit pouze v případě, že pochází z místního počítače. Proto mobilní kód by měl být bezpečnost typů.  
  
<a name="secure_library"></a>   
## <a name="using-secure-class-libraries"></a>Pomocí zabezpečené knihovny tříd  
 Pokud váš kód požadavky a je udělena oprávnění potřebná knihovna tříd, bude mít přístup do knihovny a prostředky, které zpřístupňuje knihovny bude chráněn před neoprávněným přístupem. Pokud váš kód nemá příslušná oprávnění, nebude mít přístup knihovny tříd k a škodlivý kód nebude možné použít kód nepřímý přístup k chráněným prostředkům. Jiný kód, který volá kód musí také mít oprávnění k přístupu ke knihovně. Pokud není, bude omezeno spuštěn rovněž vašeho kódu.  
  
 Zabezpečení přístupu kódu nebude odstraněn možnost lidské chyby při psaní kódu. Ale pokud vaše aplikace používá knihovny tříd zabezpečený přístup k chráněným prostředkům, bezpečnostní riziko pro kód aplikace je zmenšit, protože knihovny tříd jsou podrobně zkoumány na potenciální problémy se zabezpečením.  
  
## <a name="declarative-security"></a>Deklarativní zabezpečení  
 Syntaxe deklarativní zabezpečení využívá [atributy](../../../docs/standard/attributes/index.md) umístit informace o zabezpečení do [metadata](../../../docs/standard/metadata-and-self-describing-components.md) z vašeho kódu. Atributy mohou být umístěny na úrovni sestavení, třída nebo člen označující typ požadavku, vyžádání nebo přepsání, které chcete použít. Požadavky se používají v aplikacích, které cílí modul common language runtime k informování o oprávnění, které aplikace potřebuje nebo nechce systémem zabezpečení modulu runtime. Požadavky a přepsání se používají v knihovnách pomáhá chránit prostředky z volající nebo přepsat výchozí chování zabezpečení.  
  
> [!NOTE]
>  V [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], byly důležité změny modelu zabezpečení rozhraní .NET Framework a terminologii. Další informace o těchto změnách najdete v tématu [změny zabezpečení](../../../docs/framework/security/security-changes.md).  
  
 Chcete-li použít volání deklarativní zabezpečení, musí inicializovat data o stavu objektu oprávnění tak, aby představoval určitou formu oprávnění, které potřebujete. Každé z předdefinovaných oprávnění má atribut, který je předán <xref:System.Security.Permissions.SecurityAction> výčet popisující typ operace zabezpečení, kterou chcete provést. Oprávnění však přijmout vlastní parametry, které jsou výhradní k nim.  
  
 Následující fragment kódu ukazuje deklarativní syntaxi pro vyžádání, že volající vašeho kódu mají vlastní oprávnění nazývané `MyPermission`. Toto oprávnění je hypotetické vlastní oprávnění a neexistuje v rozhraní .NET Framework. V tomto příkladu deklarativní volání umístěno přímo před definici třídy určující, že toto oprávnění použít na úrovni třídy. Atribut je předána **SecurityAction.Demand** struktura k určení, že volající musí mít toto oprávnění, aby bylo možné spustit.  
  
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
 Imperativní syntaxe zabezpečení řeší volání zabezpečení tak, že vytvoříte novou instanci třídy oprávnění objektu, který chcete vyvolat. Imperativní syntaxi můžete provádět požadavky a přepsání, ale ne požadavků.  
  
 Před provedením volání zabezpečení, musí inicializovat data o stavu oprávnění objektu, tak, aby představoval určitou formu oprávnění, které potřebujete. Například při vytváření <xref:System.Security.Permissions.FileIOPermission> objekt, můžete použít konstruktor k chybě při inicializaci **FileIOPermission** objektu tak, aby představoval buď neomezený přístup ke všem souborům nebo žádný přístup k souborům. Nebo můžete použít jiné **FileIOPermission** objekt, předání parametrů, které označují typ přístupu, které chcete objekt představují (to znamená, číst, připojit nebo zápisu) a jaké soubory chcete objekt, který chcete chránit.  
  
 Kromě vyvolání jediného objektu zabezpečení pomocí syntaxe naléhavého zabezpečení, můžete ho k chybě při inicializaci skupiny oprávnění v sadě oprávnění. Například tato technika je jediný způsob, jak spolehlivě provést [assert](../../../docs/framework/misc/using-the-assert-method.md) volání na více oprávnění v jedné metodě. Použití <xref:System.Security.PermissionSet> a <xref:System.Security.NamedPermissionSet> třídy pro vytvoření skupiny oprávnění a pak zavolají vhodnou metodu pro vyvolání požadovaného volání zabezpečení.  
  
 Imperativní syntaxi můžete provádět požadavky a přepsání, ale ne požadavků. Může použít imperativní syntaxi pro požadavky a přepsání místo deklarativní syntaxe, když se stane pouze v době běhu známé informace, které potřebujete-li inicializovat stav oprávnění. Například pokud chcete zajistit, že volající mají oprávnění pro čtení určitého souboru, ale neznáte název tohoto souboru do doby běhu, použijte imperativní požadavky. Je také možné použít imperativní kontroly místo deklarativních, když je potřeba určit v době běhu, zda obsahuje podmínku a na základě výsledku testu, vytvořit požadavek zabezpečení (nebo ne).  
  
 Následující fragment kódu ukazuje imperativní syntaxi pro vyžádání, že volající vašeho kódu mají vlastní oprávnění nazývané `MyPermission`. Toto oprávnění je hypotetické vlastní oprávnění a neexistuje v rozhraní .NET Framework. Novou instanci třídy `MyPermision` je vytvořen v `MyMethod`, ochrana jenom tato metoda pomocí volání zabezpečení.  
  
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
 Většina aplikací a součástí (s výjimkou zabezpečených knihoven) by neměla přímo volat nespravovaný kód. Tady je několik důvodů pro tento. Pokud kód volání nespravovaného kódu přímo, ho nebude možné spustit v mnoha případech, protože kód musí být udělena vysokou úroveň důvěryhodnosti pro volání nativního kódu. Pokud jsou zásady změněny a povolit takovou aplikaci spustit, může to významně oslabit zabezpečení systému, pokud aplikace můžete provádět skoro všechny operace.  
  
 Kromě toho kód, který má oprávnění k přístupu nespravovaného kódu pravděpodobně může provádět skoro všechny operace pomocí volání nespravovaného rozhraní API. Například kód, který má oprávnění k volání nespravovaného kódu nemusí <xref:System.Security.Permissions.FileIOPermission> získat přístup k souboru; ho stačí zavolat nespravované (Win32) souboru API přímo, obcházení soubor spravované rozhraní API, která vyžaduje **FileIOPermission**. Pokud spravovaný kód má oprávnění k volání nespravovaného kódu a volají přímo do nespravovaného kódu, bude systém zabezpečení nelze spolehlivě vynutit omezení zabezpečení, protože modul runtime nemůže vynutit taková omezení na nespravovaný kód.  
  
 Pokud chcete aplikaci k provedení určité operace, která vyžaduje přístup k nespravovanému kódu, ho by to provést prostřednictvím důvěryhodné spravované třídy, které zabaluje požadovanou funkčnost (pokud taková třída existuje). Nevytvářejte obálkovou třídu sami Pokud již existuje v zabezpečené knihovny tříd. Obálková třída, která musí být poskytnuta vysoký stupeň důvěryhodnosti, může volat nespravovaný kód, je zodpovědná za náročné, že jeho volající mít příslušná oprávnění. Pokud používáte obálkovou třídu, musí váš kód pouze k vyžádání a udělit oprávnění, která vyžaduje obálková třída.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Security.PermissionSet>  
 <xref:System.Security.Permissions.FileIOPermission>  
 <xref:System.Security.NamedPermissionSet>  
 <xref:System.Security.Permissions.SecurityAction>  
 [Assert](../../../docs/framework/misc/using-the-assert-method.md)  
 [Zabezpečení přístupu kódu](../../../docs/framework/misc/code-access-security.md)  
 [Základy zabezpečení přístupu kódu](../../../docs/framework/misc/code-access-security-basics.md)  
 [Atributy](../../../docs/standard/attributes/index.md)  
 [Metadata a komponenty popisující samy sebe](../../../docs/standard/metadata-and-self-describing-components.md)
