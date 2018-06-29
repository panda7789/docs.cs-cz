### <a name="mef-catalogs-implement-ienumerable-and-therefore-can-no-longer-be-used-to-create-a-serializer"></a>MEF katalogy implementovat rozhraní IEnumerable a proto už slouží k vytvoření serializátoru

|   |   |
|---|---|
|Podrobnosti|Od verze rozhraní .NET Framework 4.5, MEF katalogy implementovat rozhraní IEnumerable a proto už slouží k vytvoření serializátoru (<xref:System.Xml.Serialization.XmlSerializer?displayProperty=name> objekt). Při pokusu o serializaci katalogu MEF vyvolá výjimku.|
|Návrh|Již nelze používat MEF k vytvoření serializátoru|
|Rozsah|Hlavní|
|Version|4.5|
|Typ|modul runtime|

