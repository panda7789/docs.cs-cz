---
title: "Metadata a komponenty popisující samy sebe"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- runtime, metadata
- languages, interoperability
- portable executable files, metadata
- self-describing files
- metadata, about metadata
- common language runtime, metadata
- PE files, metadata
- components [.NET Framework], metadata
ms.assetid: 3dd13c5d-a508-455b-8dce-0a852882a5a7
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: ac08dcf305e8cc0c1a3be3b8300ed9981e7d84d4
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="metadata-and-self-describing-components"></a>Metadata a komponenty popisující samy sebe
V minulosti součást softwaru (.exe nebo .dll), která byla zapsána v jednom jazyce nelze použít snadno softwarová součást, která byla zapsána v jiném jazyce. COM zadat krok k řešení tohoto problému. Rozhraní .NET Framework usnadňuje vzájemná spolupráce součásti i tím, že kompilátory pro vydávání další deklarativní informace do všech modulů a sestavení. Tyto informace, nazývané metadata, pomáhá součásti bezproblémově pracovat.  
  
 Metadata jsou binární informace, které popisují vaše program, který je uložený v běžné souboru přenosné spustitelný soubor (PE) runtime jazyka nebo v paměti. Při kompilaci kódu do souboru PE metadata vložena do jednoho část souboru, a váš kód je převést na Microsoft (MSIL intermediate language) a vložen do jiné části souboru. Každý typ nebo člen, který je definovaný a odkazy v modulu nebo sestavení je popsán v rámci metadat. Pokud je kód spuštěn, modul runtime načte metadata do paměti a odkazuje zjistit informace o váš kód třídy, členy, dědičnost a tak dále.  
  
 Metadata popisuje každý typ nebo člen definované ve vašem kódu způsobem jazykově neutrální. Metadata se ukládají následující informace:  
  
-   Popis sestavení.  
  
    -   Identita (název, verze, jazykové verze, veřejný klíč).  
  
    -   Typy, které jsou exportovány.  
  
    -   Další sestavení, která toto sestavení závisí na.  
  
    -   Oprávnění zabezpečení potřebné ke spuštění.  
  
-   Popis typů.  
  
    -   Název, viditelnost, základní třídy a rozhraní implementovat.  
  
    -   Členy (metody, pole, vlastnosti, události, vnořené typy).  
  
-   Atributy.  
  
    -   Další popisné prvky, které změnit typy a členy.  
  
## <a name="benefits-of-metadata"></a>Výhody metadat  
 Metadata je klíčem k jednodušší programovací model a eliminuje potřebu soubory, soubory hlaviček nebo externích metod odkazu komponenty definice jazyka IDL (Interface). Metadata umožňují rozhraní .NET Framework k popisu sami automaticky jazykově neutrální způsobem, neviditelně vývojář i uživatele. Kromě toho je rozšiřitelný prostřednictvím atributy metadat. Metadata poskytují následující hlavní výhody:  
  
-   Soubory popisující samy sebe.  
  
     Společnými moduly runtime jazyka a sestavení jsou popisující samy sebe. Metadata modulů obsahuje vše potřebné k interakci se jiný modul. Metadata automaticky poskytuje funkci IDL v modelu COM, abyste je mohli používat jeden soubor pro definice a implementace. Moduly runtime a sestavení i nevyžadují registrace s operačním systémem. V důsledku toho popisů používaných modulem runtime vždy odráží skutečný kód zkompilovaný soubor, což zvyšuje spolehlivost aplikace.  
  
-   Vzájemná funkční spolupráce jazyka a jednodušší návrhu na základě součástí.  
  
     Metadata poskytují všechny požadované informace o zkompilovaný kód, abyste třídy dědí PE soubor napsaný v jiném jazyce. Můžete vytvořit instanci libovolné třídy napsané v libovolném jazyce spravované (jakýkoli jazyk, který cílí modul common language runtime) bez obav o explicitní zařazování nebo pomocí vlastní interoperabilita kódu.  
  
-   Atributy.  
  
     Rozhraní .NET Framework umožňuje deklarovat specifické druhy metadat nazývané atributy, zkompilovaný soubor. Atributy lze nalézt v rozhraní .NET Framework a slouží k řízení podrobněji chování vašeho programu za běhu. Kromě toho můžete emitování vlastní metadata do rozhraní .NET Framework soubory pomocí uživatelsky definované vlastní atributy. Další informace najdete v tématu [atributy](../../docs/standard/attributes/index.md).  
  
## <a name="metadata-and-the-pe-file-structure"></a>Metadata a struktura přenositelného spustitelného souboru  
 Metadata se ukládají do jeden oddíl souboru rozhraní .NET Framework přenosné spustitelný soubor (PE), při Microsoft (MSIL intermediate language) je uložen v jiném oddíle PE souboru. Část metadata souboru obsahuje řadu tabulku a haldu datové struktury. Část MSIL obsahuje MSIL a metadat tokeny, které odkazují na části metadata souboru PE. Tokeny metadat může dojít, když používáte nástroje, jako [MSIL Disassembler (Ildasm.exe)](../../docs/framework/tools/ildasm-exe-il-disassembler.md) zobrazíte kódu je MSIL, např.  
  
### <a name="metadata-tables-and-heaps"></a>Metadata tabulky a haldy  
 Každá tabulka metadat obsahuje informace o elementy vašeho programu. Například jedna tabulka metadat popisuje třídy ve vašem kódu, jiná tabulka popisuje pole a tak dále. Pokud máte deset tříd ve vašem kódu, bude mít tabulka třída desítkami řádků, jeden pro každou třídu. Metadata tabulky odkazovat na jiné tabulky a haldy. Například v tabulce metadata pro třídy odkazuje na tabulku pro metody.  
  
 Metadata také ukládá informace do čtyř struktur haldy: řetězec, objekt blob, řetězec uživatelského a identifikátor GUID. Všechny řetězce používá k pojmenování typů a členů jsou uloženy v haldě řetězce. Například metoda tabulku přímo neukládá název konkrétní metody, ale odkazuje na název metody, které jsou uložené v haldě řetězce.  
  
### <a name="metadata-tokens"></a>Tokeny metadat  
 Každý řádek každé metadat tabulky je jedinečně identifikovaný v části MSIL souboru PE token metadat. Tokeny metadata jsou koncepčně podobá ukazatele uloženým v MSIL, které odkazují na konkrétní tabulku metadat.  
  
 Token metadat je číslo čtyř bajtů. Horní byte označuje tabulku metadat, ke kterému konkrétní token odkazuje (metoda, typ a tak dále). Zbývající tři bajty zadejte řádek v tabulce metadata, která odpovídá programovací element se popsané. Pokud definujete metody v jazyce C# a kompilována soubor PE, následující token metadat může existovat v části MSIL souboru PE:  
  
```  
0x06000004  
```  
  
 Horní byte (`0x06`) označuje, že je to **MethodDef** tokenu. Nižší tři bajty (`000004`) informuje modul common language runtime k prohledání čtvrtý řádek **MethodDef** tabulku pro informace, které popisuje definici této metody.  
  
### <a name="metadata-within-a-pe-file"></a>Metadata v souboru PE  
 Pokud je program kompilován pro modul common language runtime, jsou převedeny na soubor PE, který se skládá ze tří částí. Následující tabulka popisuje obsah každé části.  
  
|Část PE|Obsah PE oddílu|  
|----------------|----------------------------|  
|Záhlaví PE|Index hlavní části souboru PE a adresu vstupního bodu.<br /><br /> Modul runtime používá tyto informace k identifikaci souboru jako soubor PE a určení, kde začít provádění při načítání program do paměti.|  
|MSIL – instrukce|Microsoft převodní jazyk pokynů (MSIL) tvořící vašeho kódu. Mnoho MSIL pokyny se předěl doprovází tokenů metadat.|  
|Metadata|Tabulky a haldy metadat. Modul runtime používá k zaznamenání informací o každý typ nebo člen ve vašem kódu v této části. Tato část také obsahuje vlastní atributy a informace o zabezpečení.|  
  
## <a name="run-time-use-of-metadata"></a>Používání metadat v době běhu  
 Abyste lépe pochopili, metadat a její role v modulu CLR, může být vhodné vytvořit jednoduchý program a ilustrují, jak metadata ovlivňuje jeho život v době běhu. Následující příklad kódu ukazuje dvě metody uvnitř třídy s názvem `MyApp`. `Main` Metoda je vstupní bod programu, zatímco `Add` metoda jednoduše vrátí součet dva argumenty celé číslo.  
  
```vb  
Public Class MyApp  
   Public Shared Sub Main()  
      Dim ValueOne As Integer = 10  
      Dim ValueTwo As Integer = 20  
      Console.WriteLine("The Value is: {0}", Add(ValueOne, ValueTwo))  
   End Sub  
  
   Public Shared Function Add(One As Integer, Two As Integer) As Integer  
      Return (One + Two)  
   End Function  
End Class  
```  
  
```csharp  
using System;    
public class MyApp  
{  
   public static int Main()  
   {  
      int ValueOne = 10;  
      int ValueTwo = 20;           
      Console.WriteLine("The Value is: {0}", Add(ValueOne, ValueTwo));  
      return 0;  
   }  
   public static int Add(int One, int Two)  
   {  
      return (One + Two);  
   }  
}  
```  
  
 Při spuštění kódu, modul runtime načte modul do paměti a bere v úvahu metadata pro tuto třídu. Po načtení modulu runtime provádí rozsáhlou analýzu datového proudu (MSIL intermediate language) společnosti Microsoft metoda ji převést na pokyny rychlého nativní počítače. Modul runtime používá za běhu (JIT) kompilátor převést pokynů MSIL nativní strojového kódu v době podle potřeby.  
  
 Následující příklad ukazuje součástí MSIL vytvořené z předchozí kód `Main` funkce. Můžete zobrazit MSIL a metadat z jakékoli aplikace rozhraní .NET Framework pomocí [MSIL Disassembler (Ildasm.exe)](../../docs/framework/tools/ildasm-exe-il-disassembler.md).  
  
```  
.entrypoint  
.maxstack  3  
.locals ([0] int32 ValueOne,  
         [1] int32 ValueTwo,  
         [2] int32 V_2,  
         [3] int32 V_3)  
IL_0000:  ldc.i4.s   10  
IL_0002:  stloc.0  
IL_0003:  ldc.i4.s   20  
IL_0005:  stloc.1  
IL_0006:  ldstr      "The Value is: {0}"  
IL_000b:  ldloc.0  
IL_000c:  ldloc.1  
IL_000d:  call int32 ConsoleApplication.MyApp::Add(int32,int32) /* 06000003 */  
```  
  
 JIT kompilátor čte MSIL pro celou metodu, důkladně analyzuje je a generuje efektivní nativní pokyny pro metodu. V `IL_000d`, token metadata pro `Add` – metoda (`/*` `06000003 */`) je došlo a modul runtime používá ke konzultaci třetím řádku **MethodDef** tabulky.  
  
 V následující tabulce jsou součástí **MethodDef** tabulka odkazovaná metadata token, který popisuje `Add` metoda. Zatímco jiné tabulky metadat existovat v tomto sestavení a mít vlastní jedinečné hodnoty, je popsána pouze v této tabulce.  
  
|Řádek|Relativní virtuální adresy (RVA)|ImplFlags|Příznaky|Název<br /><br /> (Bodů na haldu řetězce.)|Podpis (body do objektu blob haldy).|  
|---------|--------------------------------------|---------------|-----------|-----------------------------------------|----------------------------------------|  
|1|0x00002050|IL<br /><br /> Spravované|Public<br /><br /> ReuseSlot<br /><br /> SpecialName<br /><br /> Příznakem RTSpecialName<br /><br /> .ctor|.ctor (konstruktor)||  
|2|0x00002058|IL<br /><br /> Spravované|Public<br /><br /> Static<br /><br /> ReuseSlot|Main|String|  
|3|0x0000208c|IL<br /><br /> Spravované|Public<br /><br /> Static<br /><br /> ReuseSlot|Přidejte|int, int, int|  
  
 Každý sloupec v tabulce obsahuje důležité informace o kódu. **RVA** sloupec umožňuje modulu runtime vypočítat adresu paměti MSIL, která definuje tuto metodu. **ImplFlags** a **příznaky** sloupce obsahují bitovou masku popisující metodu (například zda metoda je veřejný nebo privátní). **Název** sloupec indexuje název metody z haldy řetězce. **Podpis** sloupec indexuje definici signatury metody v haldě objektů blob.  
  
 Modul runtime vypočítá požadovanou adresu posunu ze **RVA** sloupec ve třetím řádku a vrátí tuto adresu kompilátoru JIT, který pak bude pokračovat na novou adresu. JIT kompilátor pokračuje ve zpracování MSIL na novou adresu, dokud zjistí další metadata token a tento proces se opakuje.  
  
 Modul runtime pomocí metadat, má přístup k veškeré informace potřebné k načtení kódu a jeho zpracování do nativní počítače pokyny. Tímto způsobem, metadata umožňuje soubory popisující samy sebe a společně s obecný systém typů dědičnosti mezi jazyky.  
  
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Atributy](../../docs/standard/attributes/index.md)|Popisuje, jak použít atributy, psát vlastní atributy a načtení informací uložených v atributech.|
