---
title: "Dispose – vzor"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Dispose method
- class library design guidelines [.NET Framework], Dispose method
- class library design guidelines [.NET Framework], Finalize method
- customizing Dispose method name
- Finalize method
ms.assetid: 31a6c13b-d6a2-492b-9a9f-e5238c983bcb
caps.latest.revision: "22"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 97f0c63857b7af408613e1ffdfecb157d1e2c704
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="dispose-pattern"></a>Dispose – vzor
Všechny programy získat jeden nebo více systémových prostředků, například paměť, popisovače systému nebo připojení databáze, v průběhu jejich provádění. Vývojáři mají být opatrní při použití takových systémové prostředky, protože musí být vydané po svém získat a použít.  
  
 Modul CLR poskytuje podporu pro automatická správa paměti. Spravované paměti (paměť přidělená pomocí operátoru jazyka C# `new`) nemusí být explicitně vydání. Je vydala automaticky modulem garbage collector (GC). Tím uvolní vývojáři z zdlouhavé a složité úlohy uvolňování paměti a musí být jedním z hlavních důvodů pro nebývalá produktivitu poskytované rozhraním .NET Framework.  
  
 Bohužel spravované paměti se právě jeden z mnoha typů prostředků systému. Prostředky než spravované paměti stále potřeba explicitně vydané a jsou označovány jako nespravované prostředky. Globální Katalog se konkrétně není navržená ke správě takové nespravované prostředky, což znamená, že odpovědnost za správu nespravované prostředky leží do nesprávných rukou vývojáři.  
  
 Modul CLR poskytuje pomoc v uvolnění nespravovaných prostředků. <xref:System.Object?displayProperty=nameWithType>deklaruje virtuální metoda <xref:System.Object.Finalize%2A> (také nazývané finalizační metodu), je volána metodou globální Katalog před paměti objektu je požadovaná globální Katalog a může být potlačena za účelem uvolnění nespravovaných prostředků. Typy, které potlačí finalizační metodu jsou označovány jako finalizable typy.  
  
 I když finalizační metody jsou platné v některých scénářích čištění, mají dvě důležité nevýhody:  
  
-   Finalizační metodu je volána, když globální Katalog zjistí, že objekt je vhodné pro kolekci. K tomu dojde při některých neurčená časovém intervalu po už není potřeba prostředek. Zpoždění mezi při může vývojář, nebo chcete verzi prostředku a čas, kdy prostředek ve skutečnosti vydal finalizační metodu může nepřijatelné v programech, které získat mnoho omezených prostředky (prostředky, které můžete snadno vyčerpán) nebo v případy, ve kterých jsou prostředky nákladná zachovat používá (například vyrovnávací paměti velkých nespravované paměti).  
  
-   Když modulu CLR potřebuje volat finalizační metody, se musí odložit kolekce paměti objektu dokud další zaokrouhlit uvolnění paměti (finalizační metody spustit mezi kolekce). To znamená, že objektu paměti (a všechny objekty, které se odkazuje) nebude vydané pro delší časové období.  
  
 Tedy spoléhat výhradně na finalizační metody nemusí být vhodné v mnoha scénářích, když je potřeba provést co nejrychleji, uvolnění nespravovaných prostředků při plánování práce s omezených prostředků, nebo vysoce původce scénářů, ve kterých přidané režii uvolňování paměti Finalizace nepřijatelné.  
  
 Poskytuje rozhraní <xref:System.IDisposable?displayProperty=nameWithType> rozhraní, které by měla být implementována zajistit vývojář manuální způsob, jak co nejrychleji nejsou potřeba uvolnění nespravovaných prostředků. Také poskytuje <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> metoda, která se dá zjistit globální Katalog, který objekt ručně vyřazena a nemusí být dokončen už, v takovém případě objektu paměť se nedá uvolnit dříve. Typy, které implementují `IDisposable` rozhraní jsou označovány jako uvolnitelné typy.  
  
 Vzor Dispose je určený pro standardizaci využití a provádění finalizační metody a `IDisposable` rozhraní.  
  
 Hlavní motivace pro vzor je ke snížení složitosti implementace <xref:System.Object.Finalize%2A> a <xref:System.IDisposable.Dispose%2A> metody. Složitost vyplývá z faktu, že metody sdílet některé, ale ne všechny cesty kódu (rozdíly jsou popsány dále v kapitole). Kromě toho jsou historických důvody pro některé prvky vzoru související s vývoj jazyková podpora pro správu prostředků deterministický.  
  
 **PROVEĎTE ✓** implementace základní Dispose vzoru na typy obsahující instance uvolnitelné typy. Najdete v článku [základní vzor Dispose](#basic_pattern) část Podrobnosti o základní vzor.  
  
 Pokud je zodpovědná za dobu životnosti jiné na jedno použití objekty typu, vývojáři potřebovat způsob, jak k uvolnění z nich, příliš. Pomocí kontejneru `Dispose` metoda je pohodlný způsob, jak to umožňují.  
  
 **PROVEĎTE ✓** implementovat základní vzor Dispose a zadejte finalizační metody pro typy prostředků podniku, které je potřeba explicitně uvolnit a které nemají finalizační metody.  
  
 Například by měla být implementována vzoru na typy ukládání nespravované paměti vyrovnávací paměti. [Finalizable typy](#finalizable_types) část popisuje pokyny týkající se implementace finalizační metody.  
  
 **✓ ZVAŽTE** implementace vzoru Dispose základní na třídách sami nemáte uložení nespravovaných prostředků nebo na jedno použití objekty jsou ale mohou mít podtypů, které provádějí.  
  
 Je to skvělý například <xref:System.IO.Stream?displayProperty=nameWithType> třídy. Přestože je abstraktní základní třída, která nebude obsahovat žádné prostředky, nezadávejte většinu jeho podtřídy a z toho důvodu se implementuje tohoto vzoru.  
  
<a name="basic_pattern"></a>   
## <a name="basic-dispose-pattern"></a>Dispose základní vzor  
 Základní implementace vzoru zahrnuje implementace `System.IDisposable` rozhraní a deklarace `Dispose(bool)` metodu, která implementuje veškerou logiku vyčištění prostředků se dělí `Dispose` metoda a volitelné finalizační metodu.  
  
 Následující příklad ukazuje jednoduchou implementaci základní vzor:  
  
```  
public class DisposableResourceHolder : IDisposable {  
  
    private SafeHandle resource; // handle to a resource  
  
    public DisposableResourceHolder(){  
        this.resource = ... // allocates the resource  
    }  
  
    public void Dispose(){  
        Dispose(true);  
        GC.SuppressFinalize(this);  
    }  
  
    protected virtual void Dispose(bool disposing){  
        if (disposing){  
            if (resource!= null) resource.Dispose();  
        }  
    }  
}  
```  
  
 Logická hodnota parametru `disposing` označuje, zda byla vyvolána metoda z `IDisposable.Dispose` implementace nebo z finalizační metodu. `Dispose(bool)` Implementace měli zkontrolovat parametr před přístupem k jiné odkaz na objekty (například pole zdroje v předchozím příkladu). Tyto objekty by měly být dostupné jenom při metoda je volána z `IDisposable.Dispose` implementace (když `disposing` rovná parametru na hodnotu true). Pokud metoda je volána z finalizační metodu (`disposing` je false), by neměl přístup k jiné objekty. Důvodem je, že objekty jsou dokončeny v nepředvídatelným pořadí a tak se ani žádné z jejich závislosti, může již mít byl dokončen.  
  
 Tato část platí také, pro třídy na bázi, který již neimplementuje vzoru Dispose. Pokud se dědí z třídy, která již implementuje vzor, jednoduše přepsat `Dispose(bool)` metody můžete zajistit logiku čištění dalších prostředků.  
  
 **PROVEĎTE ✓** deklarovat chráněné virtuální void `Dispose(bool disposing)` metoda a centralizovat veškerou logiku s uvolňováním nespravovaných prostředků.  
  
 Tato metoda by měla dojít všechny vyčištění prostředků. Metoda je volána z obou finalizační metodu a `IDisposable.Dispose` metoda. Parametr bude mít hodnotu false, pokud volané z uvnitř finalizační metody. Slouží k zajištění, že jakýkoli kód spuštěn během dokončení není přístup k jiné finalizable objekty. Podrobnosti implementace finalizační metody jsou popsané v další části.  
  
```  
protected virtual void Dispose(bool disposing){  
    if (disposing){  
        if (resource!= null) resource.Dispose();  
    }  
}  
```  
  
 **PROVEĎTE ✓** implementovat `IDisposable` rozhraní jednoduše voláním `Dispose(true)` následuje `GC.SuppressFinalize(this)`.  
  
 Volání `SuppressFinalize` by měl použít pouze v případě `Dispose(true)` úspěšně spustí.  
  
```  
public void Dispose(){  
    Dispose(true);  
    GC.SuppressFinalize(this);  
}  
```  
  
 **X nesmí** zkontrolujte bezparametrový `Dispose` metoda virtuální.  
  
 `Dispose(bool)` Metoda je ten, který by měla být potlačena podtřídy.  
  
```  
// bad design  
public class DisposableResourceHolder : IDisposable {  
    public virtual void Dispose(){ ... }  
    protected virtual void Dispose(bool disposing){ ... }  
}  
  
// good design  
public class DisposableResourceHolder : IDisposable {  
    public void Dispose(){ ... }  
    protected virtual void Dispose(bool disposing){ ... }  
}  
```  
  
 **X nesmí** deklarovat žádné přetížení `Dispose` jinak než `Dispose()` a `Dispose(bool)`.  
  
 `Dispose`měli byste zvážit vyhrazené slovo pomohou kodifikovat tohoto vzoru a nedošlo k záměně mezi implementátory informačních technologií, uživatelů a kompilátory. Některé jazyky vybrat automaticky implementovat tento vzor na určité typy.  
  
 **PROVEĎTE ✓** povolit `Dispose(bool)` metoda, která se má volat více než jednou. Zvolit metodu se nic nestane. po prvním volání.  
  
```  
public class DisposableResourceHolder : IDisposable {  
  
    bool disposed = false;  
  
    protected virtual void Dispose(bool disposing){  
        if(disposed) return;  
        // cleanup  
        ...  
        disposed = true;  
    }  
}  
```  
  
 **X nepoužívejte** došlo k výjimce z uvnitř `Dispose(bool)` nejsou pod kritických situací, kdy je proces obsahující poškozená (nevracení, nekonzistentní sdíleného stavu atd.).  
  
 Uživatelé očekávají, že který volání `Dispose` nebude vyvolat výjimku.  
  
 Pokud `Dispose` může vyvolat výjimku, nebude spustit další blok finally čištění logiky. Chcete-li tento problém obejít, bude uživatel muset zabalení každé volání `Dispose` (v rámci nakonec blokovat!) v bloku try, což vede k velmi složité čištění obslužné rutiny. Pokud provádění `Dispose(bool disposing)` metoda, nikdy throw výjimku, pokud uvolnění je false. Díky tomu bude ukončit proces, pokud provádění uvnitř kontextu finalizační metodu.  
  
 **PROVEĎTE ✓** throw <xref:System.ObjectDisposedException> z kteréhokoli člena, který nelze použít po objekt byl vyřazen.  
  
```  
public class DisposableResourceHolder : IDisposable {  
    bool disposed = false;  
    SafeHandle resource; // handle to a resource  
  
    public void DoSomething(){  
           if(disposed) throw new ObjectDisposedException(...);  
        // now call some native methods using the resource   
            ...  
    }  
    protected virtual void Dispose(bool disposing){  
        if(disposed) return;  
        // cleanup  
        ...  
        disposed = true;  
    }  
}  
```  
  
 **✓ ZVAŽTE** poskytuje metoda `Close()`, kromě `Dispose()`, pokud je zavřete standardní terminologii v oblasti.  
  
 Když to uděláte, je důležité, abyste vytvořili `Close` implementace identické `Dispose` a zvažte implementaci `IDisposable.Dispose` metoda explicitně.  
  
```  
public class Stream : IDisposable {  
    IDisposable.Dispose(){  
        Close();  
    }  
    public void Close(){  
        Dispose(true);  
        GC.SuppressFinalize(this);  
    }  
}  
```  
  
<a name="finalizable_types"></a>   
## <a name="finalizable-types"></a>Finalizable typy  
 Finalizable typy jsou typy, které rozšiřují základní vzor Dispose přepsání finalizační metodu a poskytnutím finalizace kódové cestě v `Dispose(bool)` metoda.  
  
 Finalizační metody jsou často těžké implementovat správně, především proto nelze provádět určité předpoklady (obvykle platný) o stavu systému při jejich provádění. Následující pokyny měli vzít v úvahu opatrní.  
  
 Nezapomeňte, že některé pokyny platí není právě k `Finalize` metoda, ale pro jakýkoli kód volat z finalizační metody. V případě základní Dispose vzor předtím definovaný, to znamená logiky, která provede uvnitř `Dispose(bool disposing)` při `disposing` parametr je false.  
  
 Pokud základní třídy již je finalizable a implementuje základní vzor Dispose, by neměl přepsat `Finalize` znovu. Měli byste místo toho právě přepsat `Dispose(bool)` metody můžete zajistit logiku čištění dalších prostředků.  
  
 Následující kód ukazuje příklad finalizable typu:  
  
```  
public class ComplexResourceHolder : IDisposable {  
  
    private IntPtr buffer; // unmanaged memory buffer  
    private SafeHandle resource; // disposable handle to a resource  
  
    public ComplexResourceHolder(){  
        this.buffer = ... // allocates memory  
        this.resource = ... // allocates the resource  
    }  
  
    protected virtual void Dispose(bool disposing){  
            ReleaseBuffer(buffer); // release unmanaged memory  
        if (disposing){ // release other disposable objects  
            if (resource!= null) resource.Dispose();  
        }  
    }  
  
    ~ ComplexResourceHolder(){  
        Dispose(false);  
    }  
  
    public void Dispose(){  
        Dispose(true);  
        GC.SuppressFinalize(this);  
    }  
}  
```  
  
 **X nepoužívejte** provedení finalizable typy.  
  
 Pečlivě zvažte žádné případ, ve kterém si myslíte, že je potřeba finalizační metody. Je o skutečné náklady spojené s instancemi s finalizační metody, z hlediska výkonu i kód složitost. Dáváte přednost pomocí obálky prostředků, jako třeba <xref:System.Runtime.InteropServices.SafeHandle> k zapouzdření nespravovaných prostředků, kde je to možné, v takovém případě finalizační metody stane nepotřebné protože obálku zodpovídá za vlastní vyčištění prostředků.  
  
 **X nesmí** zkontrolujte finalizable typy hodnot.  
  
 Pouze typy odkazů ve skutečnosti získat CLR dokončené, a proto bude ignorována pokusy o umístit finalizační metody na typ hodnoty. C# a C++ kompilátory vynutit toto pravidlo.  
  
 **PROVEĎTE ✓** zkontrolujte finalizable typu, pokud typ je zodpovědná za uvolnění nespravovaných zdrojů, který nemá vlastní finalizační metodu.  
  
 Při implementaci finalizační metodu, jednoduše volání `Dispose(false)` a umístěte veškerou logiku vyčištění prostředků uvnitř `Dispose(bool disposing)` metoda.  
  
```  
public class ComplexResourceHolder : IDisposable {  
  
    ~ ComplexResourceHolder(){  
        Dispose(false);  
    }  
  
    protected virtual void Dispose(bool disposing){  
        ...  
    }  
}  
```  
  
 **PROVEĎTE ✓** implementovat základní vzor Dispose u každé finalizable typu.  
  
 To poskytuje prostředky ke explicitně vyčistit deterministický tyto stejné prostředky, pro které finalizační metodu zodpovídá uživatelům typu.  
  
 **X nesmí** přístup finalizable objekty v kódové cestě finalizační metodu, protože významné riziko, že se bude mít již byl dokončen.  
  
 Například finalizable objekt, A který obsahuje odkaz na jiný objekt finalizable B v nelze použít spolehlivě B na finalizační metodu, nebo naopak. Finalizační metody se nazývají v náhodném pořadí (souborem slabé řazení záruku kritické finalizace).  
  
 Mějte také na objekty uložené v statické proměnné se získat shromažďovat v určitých bodech během uvolnění domény aplikace nebo při ukončení procesu. Přístup k statické proměnné, která odkazuje na objekt finalizable (nebo volání statickou metodu, která může používat hodnotami uloženými v statické proměnné) nemusí být bezpečné Pokud <xref:System.Environment.HasShutdownStarted%2A?displayProperty=nameWithType> vrací hodnotu true.  
  
 **PROVÉST ✓** zkontrolujte vaše `Finalize` metoda chráněný.  
  
 C#, C++ a VB.NET vývojáři nemusíte starat o to, protože kompilátory vám pomoct vynutit tyto obecné zásady.  
  
 **X nesmí** řídicí umožňují výjimky z finalizační metodu logiku, s výjimkou systému kritické chyby.  
  
 Pokud z finalizační metody je vyvolána výjimka, modul CLR se zastaví celý proces (od verze rozhraní .NET Framework verze 2.0), dalších finalizační metody brání provádění a prostředky uvolnění řízené způsobem.  
  
 **✓ ZVAŽTE** vytváření a používání objekt kritické finalizable (typu s hierarchie typů, která obsahuje <xref:System.Runtime.ConstrainedExecution.CriticalFinalizerObject>) pro situace, ve kterých finalizační metody absolutně musí být spuštěn i při krátkodobém uvolnění domény aplikace vynucené a přístup z více vláken zruší.  
  
 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Provedení podle oprávnění Pearson Education, Inc. z [pokynů pro návrh Framework: konvence, Idioms a vzory pro jedno použití knihovny .NET, 2. vydání](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Abrams Brada publikovaná 22 Oct 2008 pomocí Designing Effective jako součást vývoj řady Microsoft Windows.*  
  
## <a name="see-also"></a>Viz také  
 <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType>  
 <xref:System.Object.Finalize%2A?displayProperty=nameWithType>  
 [Pokyny pro návrh Framework](../../../docs/standard/design-guidelines/index.md)  
 [Obecné vzory návrhu](../../../docs/standard/design-guidelines/common-design-patterns.md)  
 [Uvolňování paměti](../../../docs/standard/garbage-collection/index.md)
