#!/usr/bin/perl 
use strict;
use warnings;
require LWP::UserAgent;
use JSON;

# Send JSON 
#./sc.pl http://localhost:3000/comic '{title=>"new web hosting" , owner=>["Vishnu VN"]}'

my $req = HTTP::Request->new( 'POST', shift );
my $json = to_json ( eval (shift));
$req->content_type('application/json');
$req->content( $json );
my $lwp = LWP::UserAgent->new;
$lwp->request( $req );
