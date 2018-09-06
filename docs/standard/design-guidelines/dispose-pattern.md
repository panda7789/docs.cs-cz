---
title: Vzor dispose
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- Dispose method
- class library design guidelines [.NET Framework], Dispose method
- class library design guidelines [.NET Framework], Finalize method
- customizing Dispose method name
- Finalize method
ms.assetid: 31a6c13b-d6a2-492b-9a9f-e5238c983bcb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ff52e17cfe4a4236e4d165c0961ca3a23fed9a72
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43864641"
---
# <a name="dispose-pattern"></a>Vzor dispose
Všechny programy získat jeden nebo více systémových prostředků, jako je například paměť, popisovače systému nebo připojení k databázi, v průběhu jejich provádění. Vývojáři musí být opatrní při používání těchto systémových prostředků, protože musí být uvolněny po svém získat a používat.  
  
 CLR poskytuje podporu pro automatická správa paměti. Spravované paměti (paměť přidělena pomocí operátoru jazyka C# `new`) nemusí být explicitně uvolněn. Uvolní se automaticky podle systému uvolňování paměti (GC). To se vaši vývojáři z únavné a složité úlohy uvolňování paměti a jestli se jeden z hlavních důvodů pro dosažení nebývalé produktivity poskytované rozhraním .NET Framework.  
  
 Bohužel spravované paměti je právě jeden z mnoha typů systémových prostředků. Prostředky než spravované paměti stále nutné explicitně uvolnit a jsou označovány jako nespravované prostředky. Uvolňování paměti konkrétně je navržená ke správě těchto nespravované prostředky, což znamená, že odpovědnost za správu nespravované prostředky spočívá v rukou vývojáře.  
  
 CLR poskytuje pomoc při uvolnění nespravovaných prostředků. <xref:System.Object?displayProperty=nameWithType> deklaruje virtuální metoda <xref:System.Object.Finalize%2A> (také nazývané finalizační metody), který je volán uvolňování paměti, než paměti objektu je uvolněn systémem uvolňování paměti a může být potlačena za účelem uvolnění nespravovaných prostředků. Typy, které přepsat finalizační metody jsou označovány jako finalizovatelný typy.  
  
 I když v některých scénářích vyčištění platí finalizační metody, mají dvě významné nevýhody:  
  
-   Finalizační metoda se volá, když uvolňování paměti zjistí, že objekt je vhodné pro kolekci. K tomu dochází v některých neurčeném časový úsek, po prostředku není už potřeba. Zpoždění mezi při vývojář může nebo chcete verzi prostředku a čas, když prostředek skutečně vydal finalizační metoda může nepřijatelné v aplikacích, které získají mnoho vzácné prostředky (prostředky, které může dojít k vyčerpání snadno) nebo v případy, ve kterých jsou prostředky nákladné zachovat používá (například vyrovnávací paměti velkých nespravované paměti).  
  
-   Když modul CLR je potřeba volat finalizační metodu, se musí odložit kolekce paměti objektu dokud zaokrouhlí na další kolekce paměti (finalizační metody spuštění mezi kolekcí). To znamená, že pro delší časové období nebude všeobecně dostupné paměti objektu (a všechny objekty, které odkazuje na).  
  
 Proto spoléhání se výhradně na finalizační metody nemusí být vhodný v případech, pokud je důležité co nejrychleji uvolnit nespravované prostředky při zpracování komplexnějších vzácné prostředky, nebo vysoce výkonné scénářů, ve kterých přidání režie uvolňování paměti Finalizace nepřijatelné.  
  
 Poskytuje rozhraní <xref:System.IDisposable?displayProperty=nameWithType> rozhraní, které by měla být implementována vybranými vývojář ruční k uvolnění nespravovaných prostředků, jakmile se v případě potřeby zapíná. Poskytuje také <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> metodu, která můžete říct, že uvolňování paměti objektu byl ručně odstraněn z a nemusí být finalizován už nepotřebujeme, v takovém případě paměti objektu se nedá uvolnit dříve. Typy, které implementují `IDisposable` rozhraní se označují jako uvolnitelné typy.  
  
 Vzor Dispose má standardizovat používání a implementace finalizační metody a `IDisposable` rozhraní.  
  
 Hlavní motivace pro vzor je ke snížení složitosti implementace <xref:System.Object.Finalize%2A> a <xref:System.IDisposable.Dispose%2A> metody. Složitost vyplývá ze skutečnosti, že metody sdílet některé, ale ne všechny cesty kódu (rozdíly jsou popsány dále v kapitole). Kromě toho jsou historických důvodů, proč některé prvky vzor souvisejícími s vývojem jazyková podpora v nástroji Správa deterministické prostředků.  
  
 **✓ DO** implementace základní Dispose vzoru na typy obsahující instance uvolnitelné typy. Zobrazit [základní vzor Dispose](#basic_pattern) podrobné informace o základní vzor.  
  
 Pokud typ je zodpovědný za dobu života jiné uvolnitelné objekty, vývojáři potřebují způsob, jak vyřadit, je moc. Pomocí kontejneru `Dispose` metoda nabízí pohodlný způsob, aby to možné.  
  
 **✓ DO** implementovat základní vzor Dispose a zadejte finalizační metody pro typy prostředků podniku, které je potřeba explicitně uvolnit a které nemají finalizační metody.  
  
 Například by měla být implementována vzoru na typy ukládání nespravované paměti vyrovnávací paměti. [Finalizovatelný typy](#finalizable_types) část popisuje pokyny týkající se implementace finalizační metody.  
  
 **✓ CONSIDER** implementace vzoru Dispose základní na třídách sami nemáte uložení nespravovaných prostředků nebo na jedno použití objekty jsou ale mohou mít podtypů, které provádějí.  
  
 Je to skvělý například <xref:System.IO.Stream?displayProperty=nameWithType> třídy. I když je abstraktní základní třídu, která nebude obsahovat žádné prostředky, proveďte většina jejích podtříd a z toho důvodu implementuje tento model.  
  
<a name="basic_pattern"></a>   
## <a name="basic-dispose-pattern"></a>Vzor Dispose pro základní  
 Zahrnuje základní implementaci modelu implementace `System.IDisposable` rozhraní a deklarační popisovač `Dispose(bool)` metody, která implementuje veškerou logiku vyčištění prostředků sdílen `Dispose` metoda a volitelné finalizační metodu.  
  
 Následující příklad ukazuje, jednoduché provedení základní vzor:  
  
```csharp
public class DisposableResourceHolder : IDisposable {  
  
    private SafeHandle resource; // handle to a resource  
  
    public DisposableResourceHolder() {  
        this.resource = ... // allocates the resource  
    }  
  
    public void Dispose() {  
        Dispose(true);  
        GC.SuppressFinalize(this);  
    }  
  
    protected virtual void Dispose(bool disposing) {  
        if (disposing) {  
            if (resource!= null) resource.Dispose();  
        }  
    }  
}  
```  
  
 Parametr logické hodnoty `disposing` označuje, zda metoda byla vyvolána z `IDisposable.Dispose` implementace nebo z finalizační metody. `Dispose(bool)` Implementace zkontrolujte parametr před přístupem k další odkaz na objekty (například pole prostředků v předchozím příkladu). Tyto objekty by měl mít přístup jenom Pokud metoda je volána z `IDisposable.Dispose` implementace (když `disposing` rovná parametru na hodnotu true). Pokud je metoda vyvolána z finalizační metody (`disposing` je false), by neměl být přístupný jiné objekty. Důvodem je, že objekty jsou dokončeny v pořadí nepředvídatelné a proto jsou, nebo žádnou z jeho závislostí, může již mít finalizován.  
  
 Tato část platí také, pro třídy na bázi již neimplementuje vzor Dispose. Pokud se dědí z třídy, která již implementuje vzor, jednoduše přepsat `Dispose(bool)` metodu k dispozici logiky vyčištění dalších prostředků.  
  
 **✓ DO** deklarovat `protected virtual void Dispose(bool disposing)` metoda a centralizovat veškerou logiku s uvolňováním nespravovaných prostředků.  
  
 V této metodě se budou objevovat všechny vyčištění prostředků. Metoda je volána z obou finalizační metody a `IDisposable.Dispose` metoda. Parametr bude hodnotu false, pokud volaná z uvnitř finalizační metodu. By měla sloužit k zajištění, že veškerý kód během finalizace není přístup k jiné dokončitelné objekty. Podrobnosti implementace finalizační metody jsou popsané v další části.  
  
```csharp
protected virtual void Dispose(bool disposing) {  
    if (disposing) {  
        if (resource!= null) resource.Dispose();  
    }  
}  
```  
  
 **✓ DO** implementovat `IDisposable` rozhraní jednoduše voláním `Dispose(true)` následuje `GC.SuppressFinalize(this)`.  
  
 Volání `SuppressFinalize` dojde pouze pokud `Dispose(true)` úspěšně spustí.  
  
```csharp
public void Dispose(){  
    Dispose(true);  
    GC.SuppressFinalize(this);  
}  
```  
  
 **X DO NOT** zkontrolujte bezparametrový `Dispose` metoda virtuální.  
  
 `Dispose(bool)` Metoda je ta, kterou by měla být přepsána podtřídami.  
  
```csharp
// bad design  
public class DisposableResourceHolder : IDisposable {  
    public virtual void Dispose() { ... }  
    protected virtual void Dispose(bool disposing) { ... }  
}  
  
// good design  
public class DisposableResourceHolder : IDisposable {  
    public void Dispose() { ... }  
    protected virtual void Dispose(bool disposing) { ... }  
}  
```  
  
 **X DO NOT** deklarovat žádné přetížení `Dispose` jinak než `Dispose()` a `Dispose(bool)`.  
  
 `Dispose` považovat za vyhrazené slovo kodifikovat tento model a prevence nejasnostem mezi implementátory, uživatelů a kompilátory. Některé jazyky mohou automaticky tento model implementovat na určitých typech.  
  
 **✓ DO** povolit `Dispose(bool)` metoda, která se má volat více než jednou. Neprovádět žádnou akci po prvním volání zvolit metodu.  
  
```csharp
public class DisposableResourceHolder : IDisposable {  
  
    bool disposed = false;  
  
    protected virtual void Dispose(bool disposing) {  
        if (disposed) return;  
        // cleanup  
        ...  
        disposed = true;  
    }  
}  
```  
  
 **X AVOID** došlo k výjimce z uvnitř `Dispose(bool)` nejsou pod kritických situací, kdy je proces obsahující poškozená (nevracení, nekonzistentní sdíleného stavu atd.).  
  
 Uživatelé očekávají, že volání `Dispose` nevyvolá výjimku.  
  
 Pokud `Dispose` může vyvolat výjimku, další logiky vyčištění závěrečný blok nebude spuštěno. Chcete-li tento problém obejít, uživatel by potřeba všechna volání `Dispose` (v rámci bloku finally!) v bloku try, což vede k velmi složité vyčištění obslužné rutiny. Pokud provádění `Dispose(bool disposing)` metoda, nikdy throw výjimku, pokud disposing má hodnotu false. Tím se ukončit proces při provádění v rámci finalizační metodu.  
  
 **✓ DO** throw <xref:System.ObjectDisposedException> z kteréhokoli člena, který nelze použít po objekt byl vyřazen.  
  
```csharp
public class DisposableResourceHolder : IDisposable {  
    bool disposed = false;  
    SafeHandle resource; // handle to a resource  
  
    public void DoSomething() {  
        if (disposed) throw new ObjectDisposedException(...);  
        // now call some native methods using the resource   
        ...  
    }  
    protected virtual void Dispose(bool disposing) {  
        if (disposed) return;  
        // cleanup  
        ...  
        disposed = true;  
    }  
}  
```  
  
 **✓ CONSIDER** poskytuje metoda `Close()`, kromě `Dispose()`, pokud je zavřete standardní terminologii v oblasti.  
  
 Pokud tak učiníte, je důležité, abyste si udělali `Close` identické s implementací `Dispose` a zvažte implementaci `IDisposable.Dispose` metoda explicitně.  
  
```csharp
public class Stream : IDisposable {  
    IDisposable.Dispose() {  
        Close();  
    }  
    public void Close() {  
        Dispose(true);  
        GC.SuppressFinalize(this);  
    }  
}  
```  
  
<a name="finalizable_types"></a>   
## <a name="finalizable-types"></a>Finalizovatelný typy  
 Finalizovatelný typy jsou typy, které rozšiřují základní vzor Dispose přepisuje finalizační metody a poskytnutím finalizace kódové cestě v `Dispose(bool)` metody.  
  
 Finalizační metody je známo, že těžké implementovat správně, především, protože je nelze předem určité domněnky (obvykle platný) o stavu systému při jejich provádění. Podle následujících pokynů byste vzít v úvahu opatrní.  
  
 Všimněte si, že některé pokyny platí není jen pro `Finalize` metody, ale pro libovolný kód volá z finalizační metody. V případě základní Dispose vzor dříve definované, to znamená, že logiky, která provede uvnitř `Dispose(bool disposing)` při `disposing` parametr má hodnotu false.  
  
 Pokud základní třídy už je finalizovatelný a implementuje základní vzor Dispose, by neměla přepsat `Finalize` znovu. Měli byste místo toho jenom přepsat `Dispose(bool)` metodu k dispozici logiky vyčištění dalších prostředků.  
  
 Následující kód ukazuje příklad finalizovatelný typu:  
  
```csharp
public class ComplexResourceHolder : IDisposable {  
  
    private IntPtr buffer; // unmanaged memory buffer  
    private SafeHandle resource; // disposable handle to a resource  
  
    public ComplexResourceHolder() {  
        this.buffer = ... // allocates memory  
        this.resource = ... // allocates the resource  
    }  
  
    protected virtual void Dispose(bool disposing) {  
            ReleaseBuffer(buffer); // release unmanaged memory  
        if (disposing) { // release other disposable objects  
            if (resource!= null) resource.Dispose();  
        }  
    }  
  
    ~ComplexResourceHolder() {
        Dispose(false);  
    }  
  
    public void Dispose() {
        Dispose(true);  
        GC.SuppressFinalize(this);  
    }  
}  
```  
  
 **X AVOID** provedení finalizable typy.  
  
 Pečlivě zvažte, případ, ve kterém si myslíte, že je potřeba finalizační metodu. Se o skutečné náklady spojené s instancí s finalizační metody, z hlediska výkonu a kód složitost. Dáváte přednost, například pomocí obálky prostředků <xref:System.Runtime.InteropServices.SafeHandle> pro zapouzdření nespravovaných prostředků, kde je to možné, v takovém případě finalizační metodu stane nepotřebné vzhledem k tomu, že obálky je zodpovědná za své vlastní vyčištění prostředků.  
  
 **X DO NOT** zkontrolujte finalizable typy hodnot.  
  
 Pouze typy odkazů ve skutečnosti získat dokončí modulem CLR, a proto se bude ignorovat jakékoli pokusy o finalizační metody umístit na typ hodnoty. C# a C++ kompilátory vynucují toto pravidlo.  
  
 **✓ DO** zkontrolujte finalizable typu, pokud typ je zodpovědná za uvolnění nespravovaných zdrojů, který nemá vlastní finalizační metodu.  
  
 Při implementaci finalizační metodu, jednoduše zavolejte `Dispose(false)` a umístěte veškerou logiku vyčištění prostředků uvnitř `Dispose(bool disposing)` metody.  
  
```csharp
public class ComplexResourceHolder : IDisposable {  
  
    ~ComplexResourceHolder() {
        Dispose(false);  
    }  
  
    protected virtual void Dispose(bool disposing) {
        ...  
    }  
}  
```  
  
 **✓ DO** implementovat základní vzor Dispose u každé finalizable typu.  
  
 Díky tomu uživatelé typu prostředek pro explicitně deterministické vyčištění tyto stejné prostředky, pro které je zodpovědný finalizační metodu.  
  
 **X DO NOT** přístup finalizable objekty v kódové cestě finalizační metodu, protože významné riziko, že se bude mít již byl dokončen.  
  
 Například finalizovatelný objekt A, který odkazuje na jiný finalizovatelný objekt B nelze použít spolehlivě B v příslušné finalizační metodu, nebo naopak. Finalizační metody jsou volány v náhodném pořadí (nemá slabé řazení záruku kritická dokončení).  
  
 Také mějte na paměti, že objekty uložené ve statické proměnné získat neshromáždí v určitých bodech během uvolnění domény aplikace nebo při ukončení procesu. Přístup k statická proměnná, která odkazuje na finalizovatelný objekt (nebo zavolání statické metody, která může používat hodnotám uloženým ve statické proměnné) nemusí být bezpečné if <xref:System.Environment.HasShutdownStarted%2A?displayProperty=nameWithType> vrací hodnotu true.  
  
 **✓ DO** zkontrolujte vaše `Finalize` metoda chráněný.  
  
 Vývojáře v C#, C++ a VB.NET nemusíte starat o to, protože umožňují kompilátory vynucují toto pravidlo.  
  
 **X DO NOT** řídicí umožňují výjimky z finalizační metodu logiku, s výjimkou systému kritické chyby.  
  
 Pokud z finalizační metody, je vyvolána výjimka, modul CLR se vypne celý proces (od verze rozhraní .NET Framework verze 2.0), bránit v provádění a prostředkům se vydávají ve kontrolovaně jiných finalizační metody.  
  
 **✓ CONSIDER** vytváření a používání objekt kritické finalizable (typu s hierarchie typů, která obsahuje <xref:System.Runtime.ConstrainedExecution.CriticalFinalizerObject>) pro situace, ve kterých finalizační metody absolutně musí být spuštěn i při krátkodobém uvolnění domény aplikace vynucené a přístup z více vláken zruší.  
  
 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Přetištěno podle oprávnění Pearson vzdělávání, Inc. z [pokyny k návrhu architektury: konvence, Idiomy a vzory pro opakovaně použitelného knihovny .NET, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Brad Abrams publikované 22 Oct 2008, Designing Effective jako části této série Microsoft Windows Development.*  
  
## <a name="see-also"></a>Viz také:

- <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType>  
- <xref:System.Object.Finalize%2A?displayProperty=nameWithType>  
- [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)  
- [Obecné vzory návrhu](../../../docs/standard/design-guidelines/common-design-patterns.md)  
- [Uvolňování paměti](../../../docs/standard/garbage-collection/index.md)
