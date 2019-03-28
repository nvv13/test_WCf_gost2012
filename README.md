# test_WCf_gost2012


попробовал доработать Xades.dll Microsoft.Xades.dll из проекта
https://github.com/Good-Samaritan/signature-demo-net

мне нужно для проекта на WCF только 
Xades.dll 
Microsoft.Xades.dll 


1)сделал на
Тестовый УЦ ООО "КРИПТО-ПРО" 
https://testca2012.cryptopro.ru/ui/1/Login.aspx

сертификат
ГОСТ Р 34.10-2012 256 бит


2)поменял, строчки
в 2-х исходниках


.\signature-demo-net-master\Xades-master\Source\Library\XadesSignedXml.cs

            // reference.DigestMethod = "http://www.w3.org/2001/04/xmldsig-more#gostr3411";
            reference.DigestMethod = "urn:ietf:params:xml:ns:cpxmlsec:algorithms:gostr34112012-256";

                //reference2.DigestMethod = "http://www.w3.org/2001/04/xmldsig-more#gostr3411";
                reference2.DigestMethod = "urn:ietf:params:xml:ns:cpxmlsec:algorithms:gostr34112012-256";



.\signature-demo-net-master\Xades\Implementations\GostCryptoProvider.cs

            /*{ "http://www.w3.org/2001/04/xmldsig-more#gostr3411", "GOST3411" }*/
            { "urn:ietf:params:xml:ns:cpxmlsec:algorithms:gostr34102012-gostr34112012-256" , "GOST3411_2012_256" }

            return CPSignedXml.XmlDsigGost3410_2012_256Url; // XmlDsigGost3410UrlObsolete;

            return CPSignedXml.XmlDsigGost3411_2012_256Url; // XmlDsigGost3411UrlObsolete;

        var provider = (Gost3410_2012_256CryptoServiceProvider)certificate.PrivateKey;

        if (certificate.PrivateKey is Gost3410_2012_256CryptoServiceProvider)
        {
pragma warning disable 612
            var signatureDescription = (SignatureDescription)CryptoConfig.CreateFromName(CPSignedXml.XmlDsigGost3410_2012_256Url);

        return HashAlgorithm.Create("GOST3411_2012_256"); // "GOST3411");
....



3)после компеляции заменил Xades.dll и Microsoft.Xades.dll 

