---
title: Kolekční sestavení pro generování dynamických typů
description: ''
ms.date: 08/29/2017
helpviewer_keywords:
- reflection, dynamic assembly
- assemblies, collectible
- collectible assemblies, retrieving
ms.openlocfilehash: 85eacff22cf2e1c0b8c3d74a4971de035dfafbe4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130293"
---
# <a name="collectible-assemblies-for-dynamic-type-generation"></a>Kolekční sestavení pro generování dynamických typů

*Sestavení kolekční* jsou dynamická sestavení, která lze uvolnit bez uvolnění domény aplikace, ve které byly vytvořeny. Veškerá spravovaná a nespravovaná paměť, kterou používá kolekční sestavení, a typy, které obsahuje, mohou být uvolněny. Informace, jako je název sestavení, jsou odebrány z interní tabulky.

Chcete-li povolit uvolnění, při vytváření dynamického sestavení použijte příznak <xref:System.Reflection.Emit.AssemblyBuilderAccess.RunAndCollect?displayProperty=nameWithType>. Sestavení je přechodné (to znamená, nemůže být uloženo) a podléhá omezením popsaným v části [omezení pro sestavení kolekční](#restrictions-on-collectible-assemblies) . Modul CLR (Common Language Runtime) uvolní sestavení kolekční automaticky při uvolnění všech objektů přidružených k sestavení. Ve všech ostatních ohledech se kolekční sestavení vytvářejí a používají stejným způsobem jako ostatní dynamická sestavení.

## <a name="lifetime-of-collectible-assemblies"></a>Doba života kolekční sestavení

Životnost sestavení kolekční je řízena existencí odkazů na typy, které obsahuje, a objekty, které jsou vytvořeny z těchto typů. Modul CLR (Common Language Runtime) neuvolní sestavení, pokud existuje jeden nebo více z následujících typů (`T` je jakýkoli typ, který je definován v sestavení): 

- Instance `T`.

- Instance pole `T`.
 
- Instance obecného typu, který má `T` jako jeden z jeho argumentů typu. To zahrnuje obecné kolekce `T`, a to i v případě, že je kolekce prázdná.

- Instance <xref:System.Type> nebo <xref:System.Reflection.Emit.TypeBuilder>, která představuje `T`. 

   > [!IMPORTANT]
   > Je nutné uvolnit všechny objekty, které reprezentují části sestavení. <xref:System.Reflection.Emit.ModuleBuilder> definující `T` zachovává odkaz na <xref:System.Reflection.Emit.TypeBuilder>a objekt <xref:System.Reflection.Emit.AssemblyBuilder> uchovává odkaz na <xref:System.Reflection.Emit.ModuleBuilder>, takže odkazy na tyto objekty musí být uvolněny. Dokonce i existence <xref:System.Reflection.Emit.LocalBuilder> nebo <xref:System.Reflection.Emit.ILGenerator> používaného při vytváření `T` brání vykládku.

- Statický odkaz na `T` jiným dynamicky definovaným typem `T1`, který je stále dosažitelný spuštěním kódu. Například `T1` může odvozovat z `T`nebo `T` může být typ parametru v metodě `T1`.
 
- Typ **ByRef** ke statickému poli, které patří do `T`.

- <xref:System.RuntimeTypeHandle>, <xref:System.RuntimeFieldHandle>nebo <xref:System.RuntimeMethodHandle>, které odkazují na `T` nebo na součást `T`.

- Instance libovolného objektu reflexe, který může být použit nepřímo nebo přímo pro přístup k objektu <xref:System.Type>, který představuje `T`. Například objekt <xref:System.Type> pro `T` lze získat z typu pole, jehož typ elementu je `T`nebo z obecného typu, který má `T` jako argument typu. 

- Metoda `M` v zásobníku volání libovolného vlákna, kde `M` je metoda `T` nebo metoda na úrovni modulu, která je definována v sestavení.

- Delegát pro statickou metodu, která je definována v modulu sestavení.

Pokud pouze jedna položka z tohoto seznamu existuje pouze pro jeden typ nebo jednu metodu v sestavení, modul runtime nemůže uvolnit sestavení.

> [!NOTE]
> Modul runtime ve skutečnosti nenačítá sestavení, dokud nejsou spuštěny finalizační metody pro všechny položky v seznamu.

Pro účely sledování životního cyklu se konstruovaný obecný typ, například `List<int>` (in C#) nebo `List(Of Integer)` (v Visual Basic), který je vytvořen a použit při generování sestavení kolekční, je považován za definovaný buď v sestavení, které obsahuje definice obecného typu nebo v sestavení, které obsahuje definici jednoho z jeho typů argumentů. Přesné sestavení, které je použito, je podrobné informace o implementaci a může se změnit.
 
## <a name="restrictions-on-collectible-assemblies"></a>Omezení pro kolekční sestavení

Následující omezení platí pro kolekční sestavení: 

- **Statické odkazy**   
  Typy v běžném dynamickém sestavení nemohou mít statické odkazy na typy, které jsou definovány v sestavení kolekční. Například pokud definujete běžný typ, který dědí z typu v sestavení kolekční, je vyvolána výjimka <xref:System.NotSupportedException>. Typ v sestavení kolekční může mít statické odkazy na typ v jiném sestavení kolekční, ale rozšiřuje životnost odkazovaného sestavení na životnost odkazujícího sestavení.

-   **zprostředkovatele komunikace s objekty COM**  
   V rámci kolekční sestavení nelze definovat žádná rozhraní modelu COM a žádné instance typů v rámci sestavení kolekční nelze převést na objekty modelu COM. Typ v sestavení kolekční nemůže sloužit jako obálka s možnou modelem COM (doleva) nebo obálka s možnou (RCW). Typy v sestaveních kolekční však mohou používat objekty, které implementují rozhraní COM.

-   **volání platformy**  
   Metody, které mají atribut <xref:System.Runtime.InteropServices.DllImportAttribute>, nebudou zkompilovány, pokud jsou deklarovány v sestavení kolekční. Instrukci <xref:System.Reflection.Emit.OpCodes.Calli?displayProperty=nameWithType> nelze použít při implementaci typu v sestavení kolekční a takové typy nelze zařadit do nespravovaného kódu. Do nativního kódu však můžete zavolat pomocí vstupního bodu, který je deklarován v sestavení bez kolekční.
 
- **Zařazování**   
   Objekty (zejména Delegáti), které jsou definovány v sestaveních kolekční, nelze zařadit. Toto je omezení pro všechny přechodné emitované typy.

- **Načítání  sestavení**  
   Generování reflexe je jediným mechanismem, který je podporován pro načítání sestavení kolekční. Sestavení, která jsou načtena pomocí jakékoliv jiné formy načítání sestavení, nelze uvolnit.
 
- **Objekty vázané na kontext**    
   Kontext – statické proměnné nejsou podporovány. Typy v sestavení kolekční nemůžou <xref:System.ContextBoundObject>rozšířily. Nicméně kód v sestaveních kolekční může používat kontextově vázané objekty, které jsou definovány jinde.

-       **statických dat z vlákna**  
   Proměnné statických vláken nejsou podporovány.

## <a name="see-also"></a>Viz také:

- [Generování dynamických metod a sestavení](emitting-dynamic-methods-and-assemblies.md)
