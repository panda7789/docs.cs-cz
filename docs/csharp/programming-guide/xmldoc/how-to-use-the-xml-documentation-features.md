---
title: 'Postupy: Použití funkcí dokumentace XML (Průvodce programováním v C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- XML documentation [C#]
- C# language, XML documentation features
ms.assetid: 8f33917b-9577-4c9a-818a-640dbbb0b399
ms.openlocfilehash: 6c7e30d23868959145e8941057f1c633fe6e374e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-the-xml-documentation-features-c-programming-guide"></a>Postupy: Použití funkcí dokumentace XML (Průvodce programováním v C#)
Následující příklad obsahuje základní přehled typu, který byly dokumentovány.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csProgGuideDocComments#15](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/how-to-use-the-xml-documentation-features_1.cs)]  
  
 **Tento soubor .xml se vygeneroval s předchozí ukázka kódu.**  
**\<? xml verze = "1.0"? >**  
**\<doc >**  
 **\<sestavení >**  
 **\<název > xmlsample \< /name >**  
 **\</Assembly >**  
 **\<členy >**  
 **\<Název člena = "T:SomeClass" >**  
 **\<Souhrn >**  
 **Sem zadejte třída úrovni souhrnu dokumentace. \<nebo souhrnných >**  
 **\<Poznámky >**  
 **Může být přidružen typ nebo člen delší komentáře**  
 **pomocí značky poznámky \< /remarks >**  
 **\</member >**  
 **\<člen name="F:SomeClass.m_Name" >**  
 **\<Souhrn >**  
 **Úložiště pro vlastnost název\<nebo souhrnných >**  
 **\</member >**  
 **\<Název člena = "M:SomeClass. #ctor" >**  
 **\<Souhrn > konstruktoru třídy. \<nebo souhrnných >**  
 **\</member >**  
 **\<člen name="M:SomeClass.SomeMethod(System.String)" >**  
 **\<Souhrn >**  
 **Popis SomeMethod. \<nebo souhrnných >**  
 **\<Název parametru = "s" > zde bude parametr popis s\</param >**  
 **\<Viz také cref="T:System.String" >**  
 **Cref – atribut v libovolné značky můžete použít tak, aby odkazovaly na typ nebo člen**  
 **a kompilátor zkontroluje, zda existuje odkaz na. \</seealso >**  
 **\</member >**  
 **\<člen name="M:SomeClass.SomeOtherMethod" >**  
 **\<Souhrn >**  
 **Jiné metody. \<nebo souhrnných >**  
 **\<Vrátí >**  
 **Jsou vráceny výsledky popsané prostřednictvím vrátí značky.  \< /vrátí >**  
 **\<Viz také cref="M:SomeClass.SomeMethod(System.String)" >**  
 **Všimněte si použití atributu cref – Chcete-li konkrétní metody \</seealso >**  
 **\</member >**  
 **\<člen name="M:SomeClass.Main(System.String[])" >**  
 **\<Souhrn >**  
 **Vstupní bod pro aplikaci.**  
 **\</ souhrnné >**  
 **\<Název parametru = "argumentů" > seznam argumentů příkazového řádku\</param >**  
 **\</member >**  
 **\<člen name="P:SomeClass.Name" >**  
 **\<Souhrn >**  
 **Name – vlastnost \<nebo souhrnných >**  
 **\<Hodnota >**  
 **Hodnota značky je používán k popisu hodnota vlastnosti \< /value >**  
 **\</member >**  
 **\</Members >**  
**\</ doc >**   
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Kompilace v příkladu, zadejte následující příkaz:  
  
 `csc XMLsample.cs /doc:XMLsample.xml`  
  
 Tím se vytvoří soubor XML XMLsample.xml, které lze zobrazit v prohlížeči nebo pomocí příkazu typu.  
  
## <a name="robust-programming"></a>Robustní programování  
 Dokumentace XML začíná / / / Když vytvoříte nový projekt, uveďte průvodců některé starter / / / řádků v za vás. Zpracování tyto komentáře má určitá omezení:  
  
-   V dokumentaci musí být ve správném formátu XML. Pokud není ve správném formátu XML, se generuje upozornění a dokumentaci soubor bude obsahovat komentář, který uvádí, že došlo k chybě.  
  
-   Vývojáři mohou vytvořit vlastní sadu značky. Existuje sada doporučené značky (naleznete v části Další čtení). Některé z doporučené značky mají zvláštní význam:  
  
    -   \<Param > Značka se používá k popisu parametry. Pokud se používá, kompilátor ověří, zda parametr existuje a že všechny parametry jsou popsané v dokumentaci. Pokud ověření selže, vydá upozornění.  
  
    -   `cref` Atributu může být připojen k žádné značky, které poskytují odkaz na element kódu. Kompilátor bude ověřte, zda tento element kódu existuje. Pokud ověření selže, vydá upozornění. Kompilátor respektuje žádné `using` příkazy při vypadá pro typ popsané v `cref` atribut.  
  
    -   \<Souhrnné > Značka se používá technologii IntelliSense v sadě Visual Studio a zobrazte další informace o typ nebo člen.  
  
        > [!NOTE]
        >  Soubor XML neposkytuje úplné informace o typu a členy (například neobsahuje žádné informace o typu). Chcete-li získat úplné informace o typ nebo člen, musí být souborů dokumentace použít současně s reflexe na skutečný typ nebo člen.  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [/ DOC (možnosti kompilátoru C#)](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)  
 [Dokumentační komentáře XML](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)
