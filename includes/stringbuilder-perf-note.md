Pomocí znakový indexování s <xref:System.Text.StringBuilder.Chars%2A> vlastnost může být velmi pomalé za následujících podmínek:

- <xref:System.Text.StringBuilder> Instance je velký (například obsahuje několik desítkami tisíc znaků).
- <xref:System.Text.StringBuilder> Je "rozsekaně." To znamená, jako například opakovaná volání metody <xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType> mají automaticky rozšířena objektu <xref:System.Text.StringBuilder.Capacity%2A?displayProperty=nameWithType> vlastnost a přidělené nové bloky paměti k němu.

Protože každý znak přístup provede celou odkazovaného seznamu bloků dat najít správný vyrovnávací paměť k indexování do je závažný dopad výkon.

> [!NOTE]
>  I pro velké "rozsekaně" <xref:System.Text.StringBuilder> objektu, pomocí <xref:System.Text.StringBuilder.Chars%2A> vlastnost pro přístup na základě indexu na jeden nebo malý počet znaků má dopad na výkon zanedbatelný, obvykle je **0(n)** operaci. Dopad na výkon významné nastane, když iterace znakům <xref:System.Text.StringBuilder> objekt, který je **O(n^2)** operaci. 

Pokud narazíte na problémy s výkonem při použití znakový indexování s <xref:System.Text.StringBuilder> objekty, můžete použít některou z následujících řešení:

- Převést <xref:System.Text.StringBuilder> instance k <xref:System.String> voláním <xref:System.Text.StringBuilder.ToString%2A> metoda, pak přístup ke znakům v řetězci.

- Zkopírujte obsah existující <xref:System.Text.StringBuilder> předem velikost objektu na nový <xref:System.Text.StringBuilder> objektu. Zvyšuje výkon, protože nové <xref:System.Text.StringBuilder> objekt není rozsekaně. Příklad:

   ```csharp
   // sbOriginal is the existing StringBuilder object
   var sbNew = new StringBuilder(sbOriginal.ToString(), sbOriginal.Length);
   ```
   ```vb
   ' sbOriginal is the existing StringBuilder object
   Dim sbNew = New StringBuilder(sbOriginal.ToString(), sbOriginal.Length)
   ```
- Nastavit počáteční kapacitu <xref:System.Text.StringBuilder> objekt, který má hodnotu, která je přibližně stejné očekávanou velikost voláním <xref:System.Text.StringBuilder.%23ctor(System.Int32)> konstruktor. Všimněte si, že to přiděluje celý blok paměti, i když <xref:System.Text.StringBuilder> zřídka dosáhne své maximální kapacity.
